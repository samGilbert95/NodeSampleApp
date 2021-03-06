# build-essential Cookbook CHANGELOG

This file is used to list changes made in each version of the build-essential cookbook.

## 8.0.4 (2017-11-29)

- Install gcc-c and gcc-c++ for solaris 11
- Fix dokken's amazonlinux configuration
- Update chef dependency in metadata.rb to Chef 12.7
- Clean up testing

## 8.0.3 (2017-05-30)

- Fix solaris metadata in metadata.rb
- Remove mac_os_x_server from metata as it's not a platform

## 8.0.2 (2017-05-06)

- Remove buggy action_class.class_eval usage

## 8.0.1 (2017-04-14)

- Test with local delivery and not Rake
- Ensure compatibility with Chef 12.5
- Update apache2 license string
- Ensure compatibility with Amazon Linux on Chef 13

## 8.0.0 (2017-02-14)

- Require 12.5 or later and remove compat_resource cookbook dependency

## 7.0.3 (2016-12-22)

- Require the latest compat_resource
- Cookstyle fixes

## 7.0.2 (2016-11-07)

- Fix softwareupdate issue from -v to --verbose

## 7.0.1 (2016-10-06)

- Install gcc 4.8 on SUSE < 12

## 7.0.0 (2016-09-30)

- Remove support for OS X < 10.9 and add support for OS X 10.12
- Refactor the xcode installer resource as a custom resource that does not require updates for each new OS X update
- Use a test recipe with apt_update to avoid needing apt

## 6.0.6 (2016-09-19)

- Remove chef 11 compatibility in the metadata
- Solaris 11 needs both make and gnu make

## 6.0.5 (2016-09-07)

- Testing updates
- Require the latest compat_resource

## 6.0.4 (2016-08-19)

- Install CLTools from dmg with -allowUntrusted on old OSX
- Switch to cookstyle for ruby linting
- Add OS X hosts to the kitchen config
- Remove chefdk included gems from the Gemfile
- Better handle kitchen failures in the Rakefile
- Perform all unit/linting in a single travis job

## v6.0.3 (2016-07-26)

- Fix how gcc version specified for Solaris 11

## v6.0.2 (2016-07-22)

- Properly warn on Solaris 10
- Specify the verson of gcc to install on Solaris 11

## v6.0.1 (2016-07-19)

- Clarify that this cookbook actually required Chef 12.1 or later not 12.0 or later
- Add chef_version metadata

## v6.0.0 (2016-06-03)

This cookbook now uses the new msys2 based compiler toolchain on windows. Both 32-bit DW2 and 64-bit SEH based toolchains are available based on the gcc 5.3x series compiler. By default these are located in C:\msys2\mingw32 and C:\msys2\mingw64

## v5.0.0 (2016-06-03)

The cookbook now ships with a 12.5+ style custom resource 'build_essential' which performs the same work that the existing default.rb recipe. The default.rb recipe has been converted to consume that resource to provide backwards compatibility for users that use build-essential::default in their run lists or cookbooks. In converting to this custom resource support for EOL omnios has been removed and warning messages for Solaris 10 users have been removed. See the readme for usage information on the new resource.

## v4.0.0 (2016-05-12)

### Breaking change

This cookbook now requires Chef 12 or later as it includes the new mingw cookbook for installing Windows compilers. Mingw includes 12.5 style custom resources, which will fail to compile on Chef 11\. If you are not running Chef 12 you'll need to pin to 3.x in your environment.

## v3.2.0 (2016-03-25)

This version backs out a change in the 3.0 release which attempted to install the version of kernel-devel for the current running kernel on RHEL systems. This change had several unintended consequences and we believe the best solution is to back to change out until a better solution for the original problem is developed. Several of the issues could be resolved by code updates to build-essential, but not all, which complicates rolling forward vs. a roll back. The change caused issues which Chefspec runs on cookbooks where build-essential is a dependency as Fauxhai, used by Chefspec, does not mock out node['virtualization']. Fauxhai is being updated to mock out node['virtualization'], but we'd like to make sure a ChefDK release ships with this new Fauxhai before depending on that change.

## v3.1.0 (2016-03-23)

- Install GCC 4.8 if running on OmniOS >= 151008

## v3.0.0 (2016-03-23)

- Install GCC 4.9 on FreeBSD < 10
- Install the version of kernel-devel that matches the running Kernel on RHEL
- Remove suggests 'pkgutil' from the metadata as suggests does nothing
- Properly warn the user that build-essential does not support Solaris 10 instead of just silently continuing on
- Updated specs to run against more recent OS releases
- Removed the warning for OmniOS users from the Readme as the upstream issue has been resolved
- Switch from 7-zip to seven_zip cookbook as 7-zip has been deprecated
- Add 7-zip to the system path on Windows hosts so the recipe will work out of the box
- Switch from the deprecated 7-zip cookbook to seven_zip

## v2.4.0 (2016-03-21)

- Add gettext package to RHEL / FreeBSD to match other platforms
- Fix OS X version detection logic to properly detect OS X 10.10 and 10.11

## v2.3.1 (2016-02-18)

- Restore Chef 11 compatibility and add Travis / Test Kitchen testing for Chef 11

## v2.3.0 (2016-02-17)

- Add mingw/msys based build tools for Windows

## v2.2.4 (2015-10-06)

- Add patch package on Fedora systems
- Add additional platforms to Kitchen CI
- Use Chef standard Rubocop file and resolve several issues
- Update contributing and testing docs
- Update Gemfile with the latest testing and development deps
- Add maintainers.md and maintainers.toml files
- Add chefignore file to limit the files uploaded to the Chef server
- Add source_url and issues_url metadata for Supermarket

## v2.2.3 (2015-04-15)

- Don't install omnibus-build-essential on Solaris 10 - We decided it's easier to use the old GCC that ships with Solaris 10.
- Use ChefDK for all Travis testing.

## v2.2.2 (2015-03-27)

- Update Solar 10's omnibus-build-essential to 0.0.5

## v2.2.1 (2015-03-23)

- Install GNU Patch on Solaris 11

## v2.2.0 (2015-03-18)

- [solaris] Differentiate between Solaris 10 and 11
- [solaris] Add ucb compat package
- [solaris] Solaris 10 build essential setup
- Fix metadata to use a string instead of a bool (see #56, #57)

## v2.1.3 (2014-11-18)

- Update metadata for supported versions of OS X (10.7+) as noted from
- v2.0.0 previously (#38)
- Clarify requirement to have apt package cache updated in README. (#41)
- Fix Xcode CLI installation on OS X (#50)

## v2.1.2 (2014-10-14)

- Mac OS X 10.10 Yosemite support

## v2.1.0 (2014-10-14)

- Use fully-qualified names when installing FreeBSD package

## v2.0.6 (2014-08-11)

- Use the resource form of `remote_file` to prevent context issues

## v2.0.4 (2014-06-06)

- [COOK-4661] added patch package to _rhel recipe

## v2.0.2 (2014-05-02)

- Updated documentation about older Chef versions
- Added new SVG badges to the README
- Fix a bug where `potentially_at_compile_time` fails on non-resources

## v2.0.0 (2014-03-13)

- Updated tested harnesses to use latest ecosystem tools
- Added support for FreeBSD
- Added support for installing XCode Command Line Tools on OSX (10.7, 10.8, 10.9)
- Created a DSL method for wrapping compile_time vs runtime execution
- Install additional developement tools on some platforms
- Add nicer log and warning messages with helpful information

**Potentially Breaking Changes**

- Dropped support for OSX 10.6
- OSX no longer downloads OSX GCC and uses XCode CLI tools instead
- `build_essential` -> `build-essential` in node attributes
- `compiletime` -> `compile_time` in node attributes
- Cookbook version 2.x no longer supports Chef 10.x

## v1.4.4 (2014-02-27)

- [COOK-4245] Wrong package name used for developer tools on OS X 10.9

## v1.4.2

### Bug

- **[COOK-3318](https://tickets.chef.io/browse/COOK-3318)** - Use Mixlib::ShellOut instead of Chef::ShellOut

### New Feature

- **[COOK-3093](https://tickets.chef.io/browse/COOK-3093)** - Add OmniOS support

### Improvement

- **[COOK-3024](https://tickets.chef.io/browse/COOK-3024)** - Use newer package on SmartOS

## v1.4.0

This version splits up the default recipe into recipes included based on the node's platform_family.

- [COOK-2505] - backport omnibus builder improvements

## v1.3.4

- [COOK-2272] - Complete `platform_family` conversion in build-essential

## v1.3.2

- [COOK-2069] - build-essential will install osx-gcc-installer when XCode is present

## v1.3.0

- [COOK-1895] - support smartos

## v1.2.0

- Add test-kitchen support (source repo only)
- [COOK-1677] - build-essential cookbook support for OpenSuse and SLES
- [COOK-1718] - build-essential cookbook metadata should include scientific
- [COOK-1768] - The apt-get update in build-essentials needs to be renamed

## v1.1.2

- [COOK-1620] - support OS X 10.8

## v1.1.0

- [COOK-1098] - support amazon linux
- [COOK-1149] - support Mac OS X
- [COOK-1296] - allow for compile-time installation of packages through an attribute (see README)

## v1.0.2

- [COOK-1098] - Add Amazon Linux platform support
- [COOK-1149] - Add OS X platform support
