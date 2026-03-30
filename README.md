# Custom Web Browser for Unreal Engine

An Unreal Engine plugin that layers a **Custom Web Browser** widget on top of the engine's Web Browser stack. It adds a predictable **custom URL scheme** (`uewebbrowser://`) for page-to-game messages and works with **`SWebBrowser::BindUObject`** so JavaScript can call into your C++ or Blueprint-facing code.

## Overview

Use this when you need in-game UI or tools driven by HTML/CSS/JS, but want a simple contract from the web page back into Unreal: links or `location.href` that carry structured payloads without rolling your own CEF plumbing. The plugin focuses on navigation interception and message delivery; the stock **Web Browser Widget** dependency supplies the underlying browser runtime.

![Plugins: Custom Web Browser enabled](document/image/README-overview.png)

## Requirements

- **Web Browser Widget** plugin enabled in your project (the Custom Web Browser module depends on it).
- A **C++ project** (or C++-enabled project) if you bind handlers in code; Blueprint-only workflows still need the plugin enabled as below.

## Integrating the plugin

1. Copy [`demo/Shared/Plugins/CustomWebBrowser`](demo/Shared/Plugins/CustomWebBrowser) into your project's `Plugins` folder so you have:

   ```
   YourProject
      └── Plugins
            └── CustomWebBrowser
                  └── CustomWebBrowser.uplugin
   ```

2. **C++ projects:** add **CustomWebBrowser** to `PublicDependencyModuleNames` in your game module's `*.Build.cs`:

   ```csharp
   PublicDependencyModuleNames.AddRange(new string[] { /* ... */, "CustomWebBrowser" });
   ```

3. **Blueprint-only projects:** enable the plugin under **Edit → Plugins → Project → Widgets → Custom Web Browser**.

   | ![Enabling the plugin in the editor](document/image/Integrating_Plugin_Blueprint.png) |
   | --- |

## Messaging

### Send and receive

You can send a message from the web view to `CustomWebBrowser` to drive game logic from the page.

By binding **HandleOnBeforeBrowse** to **OnBeforeNavigation**, using an `FOnBeforeBrowse` delegate, Custom Web Browser inspects navigations whose URL starts with **`uewebbrowser://`**. If the user follows such a link, **OnMessageReceived** fires with the remainder of the URL after the scheme.

Example page:

```html
<a href="uewebbrowser://action?key=value&anotherKey=anotherValue">Tap me</a>
```

Example C++ wiring:

**Header (`.h`):**

```cpp
#pragma once

#include "Blueprint/UserWidget.h"
#include "WebViewWidget.generated.h"

class UCustomWebBrowser;

UCLASS()
class DEMO_API UMainMenuWidget : public UUserWidget
{
   GENERATED_BODY()

   // ...

protected:
   UPROPERTY(BlueprintReadWrite, meta = (BindWidget))
   UCustomWebBrowser* CustomWebBrowser;

private:
   UFUNCTION()
   void OnMessageReceived(FString Message);
};
```

**Source (`.cpp`):**

```cpp
#include "Widget/CustomWebBrowser.h"

if (CustomWebBrowser != nullptr)
{
   CustomWebBrowser->OnMessageReceived.AddDynamic(this, &UMainMenuWidget::OnMessageReceived);
}

void UMainMenuWidget::OnMessageReceived(FString Message)
{
   UE_LOG(LogTemp, Warning, TEXT("%s"), *Message);
}
```

Tapping the link logs:

```
action?key=value&anotherKey=anotherValue
```

**Navigation note:** In addition to an `<a href>`, assigning `location.href` in JavaScript triggers the same path:

```js
location.href = "uewebbrowser://action?key=value&anotherKey=anotherValue";
```

### `SWebBrowser::BindUObject`

Using [`SWebBrowser::BindUObject`](https://dev.epicgames.com/documentation/en-us/unreal-engine/API/Runtime/WebBrowser/SWebBrowser/BindUObject), the Custom Web Browser instance can be exposed to the page so script can invoke Unreal-side methods directly.

Example (equivalent effect to the link above):

```js
window.ue.uewebbrowser.sendmessage("action?key=value&anotherKey=anotherValue");
```

## References

- [Unreal Engine: `SWebBrowser::BindUObject`](https://dev.epicgames.com/documentation/en-us/unreal-engine/API/Runtime/WebBrowser/SWebBrowser/BindUObject)
- [UniWebView: messaging concepts](https://docs.uniwebview.com/guide/messaging-system.html) (similar pattern; third-party documentation)
