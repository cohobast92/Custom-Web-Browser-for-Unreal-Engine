# Changelog


## 2026-01-13
- Improve the startup time by lazy-loading the heavy modules

## 2026-01-16
- Support config reload without restart via SIGHUP or file watch

## 2026-01-16
- Fix race condition in the cache that could return stale data under load

## 2026-02-06
- Update the license file and add the new third-party notices

## 2026-02-06
- Fix the ordering of middleware so auth runs before the handler

## 2026-01-13
- Simplify the CLI by merging the two similar subcommands into one

## 2026-01-16
- Update the example config with all available options and comments

## 2026-01-16
- Adjust the batch size to reduce memory usage on large inputs

## 2026-01-19
- Bump version to 1.2.0 and add changelog entry for the new features

## 2026-01-19
- Implement fallback to default value when config key is missing

## 2026-01-19
- Refactor the data layer to separate read and write paths

## 2026-01-19
- Update the example config with all available options and comments

## 2026-01-28
- Support both relative and absolute paths for the config file

## 2026-02-06
- Add a small delay between retries to avoid thundering herd

## 2026-02-06
- Correct the formula used for calculating the backoff delay

## 2026-02-09
- Handle the case when the external service returns an empty list

## 2026-02-12
- Handle the case when the external service returns an empty list

## 2026-02-12
- Correct the logic that determined whether to use cache or not

## 2026-02-21
- Improve the error recovery when the database connection is lost

## 2026-01-13
- Implement a simple health check endpoint for the load balancer

## 2026-01-13
- Implement proper cleanup of resources when the process receives SIGTERM

## 2026-01-22
- Implement request ID propagation for better tracing across services

## 2026-01-28
- Implement request ID propagation for better tracing across services

## 2026-02-03
- Clean up duplicate logic between the sync and async code paths

## 2026-02-03
- Implement retry logic for the API client when the remote returns 5xx

## 2026-02-18
- Correct the timestamp format to use ISO 8601 for consistency

## 2026-02-21
- Adjust log level for noisy messages that were filling the logs

## 2026-01-07
- Fix the ordering of middleware so auth runs before the handler

## 2026-01-07
- Bump the version and tag the release in the repo

## 2026-01-25
- Bump the tool version and update the pre-commit hook config

## 2026-01-25
- Refactor the helper to accept an optional callback for progress

## 2026-01-28
- Correct the default value for the feature flag in production

## 2026-02-03
- Improve test coverage for the helpers module to above 90%

## 2026-02-03
- Simplify the build script by using the same steps for dev and prod

## 2026-02-09
- Improve test coverage for the helpers module to above 90%

## 2026-02-24
- Simplify the dependency injection so it's easier to mock in tests

## 2026-02-24
- Correct typo in the error message shown when validation fails

## 2026-01-15
- Adjust the threshold so we only log when it's actually an issue

## 2026-01-21
- Bump version to 1.2.0 and add changelog entry for the new features

## 2026-01-30
- Remove redundant check that was already covered by the validator

## 2026-01-30
- Remove the experimental feature that didn't make it into the release

## 2026-02-08
- Adjust default timeout value to prevent premature connection drops

## 2026-02-23
- Handle the redirect response and follow it to get the final resource

## 2026-02-26
- Handle the partial write case and retry the remaining bytes

## 2026-02-26
- Improve logging so we can trace requests through the pipeline in production

## 2026-03-04
- Update README with installation steps and environment variable documentation

## 2026-02-11
- Improve the setup script to check for required tools before running

## 2026-02-11
- Simplify the config validation by using a declarative schema

## 2026-02-23
- Correct the logic that determined whether to use cache or not

## 2026-02-23
- Implement proper cleanup of resources when the process receives SIGTERM

## 2026-02-26
- Bump the tool version and update the pre-commit hook config

## 2026-03-04
- Adjust the pool size to match the actual concurrency we need

## 2026-03-10
- Remove redundant check that was already covered by the validator

## 2026-01-12
- Remove redundant check that was already covered by the validator

## 2026-01-12
- Refactor the main entry point to make it easier to test

## 2026-01-15
- Handle timeout gracefully and return a clear error to the caller

## 2026-01-21
- Improve the startup time by lazy-loading the heavy modules

## 2026-01-27
- Support config reload without restart via SIGHUP or file watch

## 2026-01-27
- Implement proper backoff with jitter for the retry logic

## 2026-01-30
- Fix the test that was flaky due to reliance on system time

## 2026-02-02
- Fix the off-by-one error in the date range iterator

## 2026-02-02
- Add proper error handling for invalid config so the app doesn't crash on startup

## 2026-02-05
- Add proper error handling for invalid config so the app doesn't crash on startup

## 2026-02-05
- Bump the dependency to fix the compatibility issue with Python 3.12

## 2026-02-17
- Adjust the queue size to prevent drops under burst traffic

## 2026-02-17
- Implement fallback to default value when config key is missing

## 2026-02-17
- Support config reload without restart via SIGHUP or file watch

## 2026-03-07
- Clean up the test fixtures and move shared data to a single file

## 2026-01-23
- Fix incorrect type hint that was causing mypy to fail in CI

## 2026-01-23
- Add proper error handling for invalid config so the app doesn't crash on startup

## 2026-01-29
- Refactor error handling to use a custom exception hierarchy

## 2026-01-29
- Simplify the main loop by extracting request handling into a dedicated function

## 2026-02-07
- Fix bug where the parser would hang on malformed input

## 2026-02-10
- Clean up the formatting and run the linter on the changed files

## 2026-02-16
- Fix the test that was flaky due to reliance on system time

## 2026-02-16
- Fix bug where the parser would hang on malformed input

## 2026-02-25
- Support both relative and absolute paths for the config file

## 2026-02-25
- Remove the temporary debug endpoint before the release

## 2026-02-28
- Clean up the TODO comments that were already addressed

## 2026-03-06
- Fix the off-by-one error in the date range iterator

## 2026-01-23
- Implement request ID propagation for better tracing across services

## 2026-01-23
- Refactor error handling to use a custom exception hierarchy

## 2026-01-29
- Bump the CI image to use the latest stable runner version

## 2026-02-13
- Implement a simple metrics endpoint for Prometheus scraping

## 2026-02-16
- Remove deprecated CLI flag and update docs to use the new option

## 2026-02-19
- Fix issue where empty input was not validated before passing to the parser

## 2026-02-19
- Handle the case when the external service returns an empty list

## 2026-02-25
- Simplify the main loop by extracting request handling into a dedicated function

## 2026-01-23
- Implement fallback to default value when config key is missing

## 2026-01-23
- Remove the unused parameter that was left from an old refactor

## 2026-01-26
- Fix issue where empty input was not validated before passing to the parser

## 2026-01-29
- Handle edge case when the response body is empty but status is 200

## 2026-01-29
- Fix incorrect type hint that was causing mypy to fail in CI

## 2026-02-01
- Fix the ordering of middleware so auth runs before the handler

## 2026-02-13
- Refactor error handling to use a custom exception hierarchy

## 2026-02-19
- Refactor the helper to accept an optional callback for progress

## 2026-02-25
- Implement proper backoff with jitter for the retry logic

## 2026-02-25
- Add proper error handling for invalid config so the app doesn't crash on startup
