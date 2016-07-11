Changelog
=========

Unreleased
----------

*Released: Unreleased*

- Added user prefix to Ansible roles.
  [tomashavlas]

- Enclosed strings into double-quotes instead of single-quotes.
  [tomashavlas]

v1.2
----

*Released: 2016-07-08*

- Refactored tests.
  [tomashavlas]

- Refactored tasks names.
  [tomashavlas]

- Replaced boolean string representations ('yes','true'/'no','false') with boolean values (true/false).
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
