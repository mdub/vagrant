---
layout: documentation
title: Changes - 0.2.x to 0.3.x
---
# Changes from Version 0.2.x to 0.3.x

Vagrant `0.2.0` was a very stable release for Vagrant. No showstopping bugs were reported
and based on the feedback in `#vagrant`, the mailing list, and twitter, people have been
using Vagrant quite successfully.

This stability allowed us to focus on refinement and new features for Vagrant `0.3.x`.
Best of all, there are **no backwards incompatible** changes in `0.3.x`

**TODO BEFORE 0.3.x RELASE: MUCH MORE TO COME**

## Improved Packaging

While Vagrant makes it easy to package (and repackage) environments for
distribution, we thought it could be easier. The major annoyance in packaging
was that the MAC address for boxes had to be extracted and packaged manually.

No more! You can now literally just do a `vagrant package` within a Vagrant
environment, and it will package a fully functional environment. You can still
include customizations and so on with the `--include` flag, and these will
continue to work as expected.

## Minor Changes

#### Specifying a Box with `vagrant init`

`vagrant init` now takes an optional argument to specify the base box. Previously,
the generated Vagrantfile used "base" as the box and this always had to be edited.
Now, if you want to use a "karmic" box, for example, just run `vagrant init karmic`.

#### Progress Bars

Importing and exporting VMs now have a nice progress bar (similar to HTTP
box adding). You can visually see the progress of these operations, instead
of blindly waiting for a few minutes. Its a minor change, but it has made
using Vagrant that much more enjoyable.

This change was made possible to do a massive change in
Vagrant's most important dependency: the [VirtualBox gem](http://github.com/mitchellh/virtualbox).
The VirtualBox gem now uses the native C interface to talk with the
VirtualBox API, rather than piggybacking on top of XML files and `VBoxManage`.

#### Chef Solo Role Support

Roles can now be used with chef solo by specifying a path to the roles
directory with `config.chef.roles_path`. Roles can then be added to the
chef run list just like chef server. For more details on how to configure
roles for chef solo, read [the official documentation](http://wiki.opscode.com/display/chef/Chef+Solo#ChefSolo-Roles).