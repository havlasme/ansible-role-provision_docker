Changelog
=========

Unreleased
----------

- Refactored tests.
  [tomashavlas]

v1.1
----

*Released: 2016-06-30*

- Assign docker container hosts to Ansible inventory only when containers are running.
  [tomashavlas]

- Created cleanup target for tests.
  [tomashavlas]

- Added `trim` filter when checking for non-empty variables in conditions.
  [tomashavlas]

- Replaced complex conditions with `changed` and `failed` filters in acceptance tests.
  [tomashavlas]

- Added `register` prefix to variables created by Ansible role.
  [tomashavlas]

- Updated minimal Ansible version to `2.0`.
  [tomashavlas]

v1.0
----

*Released: 2016-06-13*

- First public release
  [tomashavlas]
