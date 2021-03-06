## Version 1.3 (in progress)

* Reworked the way defaults are set and inherited; explicit control given to user with `->option_defaults()` [#48](https://github.com/CLIUtils/CLI11/pull/48)
* Hidden options now are based on an empty group name, instead of special "hidden" keyword [#48](https://github.com/CLIUtils/CLI11/pull/48)
* `parse` no longer returns (so `CLI11_PARSE` is always usable) [#37](https://github.com/CLIUtils/CLI11/pull/37)
* Added `remaining()` and `remaining_size()` [#37](https://github.com/CLIUtils/CLI11/pull/37)
* `allow_extras` and `prefix_command` are now valid on subcommands [#37](https://github.com/CLIUtils/CLI11/pull/37)
* Added `take_last` to only take last value passed [#40](https://github.com/CLIUtils/CLI11/pull/40)
* More detailed error messages in a few cases [#41](https://github.com/CLIUtils/CLI11/pull/41)
* Footers can be added to help [#42](https://github.com/CLIUtils/CLI11/pull/42)
* Help flags are easier to customize [#43](https://github.com/CLIUtils/CLI11/pull/43)
* Subcommand now support groups [#46](https://github.com/CLIUtils/CLI11/pull/46)
* `CLI::RuntimeError` added, for easy exit with error codes [#45](https://github.com/CLIUtils/CLI11/pull/45) 
* The clang-format script is now no longer "hidden" [#48](https://github.com/CLIUtils/CLI11/pull/48)
* The order is now preserved for subcommands (list and callbacks) [#49](https://github.com/CLIUtils/CLI11/pull/49)
* Tests now run individually, utilizing CMake 3.10 additions if possible [#50](https://github.com/CLIUtils/CLI11/pull/50)
* Failure messages are now customizable, with a shorter default [#52](https://github.com/CLIUtils/CLI11/pull/52)
* Some improvements to error codes [#53](https://github.com/CLIUtils/CLI11/pull/53)
* `require_subcommand` now offers a two-argument form and negative values on the one-argument form are more useful [#51](https://github.com/CLIUtils/CLI11/pull/51)
* Subcommands no longer match after the max required number is obtained [#51](https://github.com/CLIUtils/CLI11/pull/51)
* Unlimited options no longer prioritize over remaining/unlimited positionals [#51](https://github.com/CLIUtils/CLI11/pull/51)
* Added `->transform` which modifies the string parsed [#54](https://github.com/CLIUtils/CLI11/pull/54)
* Changed of API in validators to `void(std::string &)` (const for users), throwing providing nicer errors [#54](https://github.com/CLIUtils/CLI11/pull/54)
* Added `CLI::ArgumentMismatch` [#56](https://github.com/CLIUtils/CLI11/pull/56) and fixed missing failure if one arg expected [#55](https://github.com/CLIUtils/CLI11/issues/55)
* Support for minimum unlimited expected arguments [#56](https://github.com/CLIUtils/CLI11/pull/56)
* Single internal arg parse function [#56](https://github.com/CLIUtils/CLI11/pull/56)

## Version 1.2

* Added functional form of flag [#33](https://github.com/CLIUtils/CLI11/pull/33), automatic on C++14
* Fixed Config file search if passed on command line [#30](https://github.com/CLIUtils/CLI11/issues/30)
* Added `CLI11_PARSE(app, argc, argv)` macro for simple parse commands (does not support returning arg)
* The name string can now contain spaces around commas [#29](https://github.com/CLIUtils/CLI11/pull/29)
* `set_default_str` now only sets string, and `set_default_val` will evaluate the default string given [#26](https://github.com/CLIUtils/CLI11/issues/26)
* Required positionals now take priority over subcommands [#23](https://github.com/CLIUtils/CLI11/issues/23)
* Extra requirements enforced by Travis

## Version 1.1

* Added simple support for enumerations, allow non-printable objects [#12](https://github.com/CLIUtils/CLI11/issues/12)
* Added `app.parse_order()` with original parse order ([#13](https://github.com/CLIUtils/CLI11/issues/13), [#16](https://github.com/CLIUtils/CLI11/pull/16)) 
* Added `prefix_command()`, which is like `allow_extras` but instantly stops and returns. ([#8](https://github.com/CLIUtils/CLI11/issues/8), [#17](https://github.com/CLIUtils/CLI11/pull/17)) 
* Removed Windows warning ([#10](https://github.com/CLIUtils/CLI11/issues/10), [#20](https://github.com/CLIUtils/CLI11/pull/20))
* Some improvements to CMake, detect Python and no dependencies on Python 2 (like Python 3) ([#18](https://github.com/CLIUtils/CLI11/issues/18), [#21](https://github.com/CLIUtils/CLI11/pull/21))

## Version 1.0
* Cleanup using `clang-tidy` and `clang-format`
* Small improvements to Timers, easier to subclass Error
* Move to 3-Clause BSD license

## Version 0.9

* Better CMake named target (CLI11)
* More warnings added, fixed
* Ini output now includes `=false` when `default_also` is true
* Ini no longer lists the help pointer
* Added test for inclusion in multiple files and linking, fixed issues (rarely needed for CLI, but nice for tools)
* Support for complex numbers
* Subcommands now test true/false directly or with `->parsed()`, cleaner parse

## Version 0.8

* Moved to CLIUtils on GitHub
* Fixed docs build and a few links

## Version 0.7

* Allow comments in ini files (lines starting with `;`)
* Ini files support flags, vectors, subcommands
* Added CodeCov code coverage reports
* Lots of small bugfixes related to adding tests to increase coverage to 100%
* Error handling now uses scoped enum in errors
* Reparsing rules changed a little to accommodate Ini files. Callbacks are now called when parsing INI, and reset any time results are added.
* Adding extra utilities in full version only, `Timer` (not needed for parsing, but useful for general CLI applications).
* Better support for custom `add_options` like functions.

## Version 0.6

* Simplified parsing to use `vector<string>` only
* Fixed fallthrough, made it optional as well (default: off): `.fallthrough()`.
* Added string versions of `->requires()` and `->excludes()` for consistency.
* Renamed protected members for internal consistency, grouped docs.
* Added the ability to add a number to `.require_subcommand()`.

## Version 0.5

* Allow `Hidden` options.
* Throw `OptionAlreadyAdded` errors for matching subcommands or options, with ignore-case included, tests
* `->ignore_case()` added to subcommands, options, and `add_set_ignore_case`. Subcommands inherit setting from parent App on creation.
* Subcommands now can be "chained", that is, left over arguments can now include subcommands that then get parsed. Subcommands are now a list (`get_subcommands`). Added `got_subcommand(App_or_name)` to check for subcommands.
* Added `.allow_extras()` to disable error on failure. Parse returns a vector of leftover options. Renamed error to `ExtrasError`, and now triggers on extra options too.
* Added `require_subcommand` to `App`, to simplify forcing subcommands. Do **not** do `add_subcommand()->require_subcommand`, since that is the subcommand, not the master `App`.
* Added printout of ini file text given parsed options, skips flags.
* Support for quotes and spaces in ini files
* Fixes to allow support for Windows (added Appveyor) (Uses `-`, not `/` syntax)

## Version 0.4

* Updates to help print
* Removed `run`, please use `parse` unless you subclass and add it
* Supports ini files mixed with command line, tested
* Added Range for further Plumbum compatibility
* Added function to print out ini file

## Version 0.3

* Added `->requires`, `->excludes`, and `->envname` from [Plumbum](http://plumbum.readthedocs.io/en/latest/)
* Supports `->mandatory` from Plubmum
* More tests for help strings, improvements in formatting
* Support type and set syntax in positionals help strings
* Added help groups, with `->group("name")` syntax
* Added initial support for ini file reading with `add_config` option.
* Supports GCC 4.7 again
* Clang 3.5 now required for tests due to googlemock usage, 3.4 should still work otherwise
* Changes `setup` for an explicit help bool in constructor/`add_subcommand`

## Version 0.2

* Moved to simpler syntax, where `Option` pointers are returned and operated on
* Removed `make_` style options
* Simplified Validators, now only requires `->check(function)`
* Removed Combiners
* Fixed pointers to Options, stored in `unique_ptr` now
* Added `Option_p` and `App_p`, mostly for internal use
* Startup sequence, including help flag, can be modified by subclasses

## Version 0.1

Initial version


