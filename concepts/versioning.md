# Versioning

As with every API we will be releasing new versions from time to time. We do promise to adhere to the following API contract:

- No value types or fields will be changed or deleted in the same API version
- What we will change within the same API version:
  - add new fields to an object
  - add new API endpoints
  - required fields can become optional
  - endpoints can become deprecated

In case we introduce breaking changes we will adjust the API base path to reflect each new major version.
