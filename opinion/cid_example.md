An example of CID in python looks something like:

- <app_module_name>/
  - routes/
    - user.py
  - lib/
    - user.py
  - clients/
    - user.py

## routes/user.py

The routes methods should be very light.

the code in routes should just be wrappers of functionality in the lib/ module. the code in routes should handle:

- deserialization of logic
- any further validation necessary
- converting format to work with lib/ directory.

That way, no one has to reach out to routes/ to use functionality: they just call the appropriate lib/ method instead.
