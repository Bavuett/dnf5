..
    Copyright Contributors to the libdnf project.

    This file is part of libdnf: https://github.com/rpm-software-management/libdnf/

    Libdnf is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 2 of the License, or
    (at your option) any later version.

    Libdnf is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with libdnf.  If not, see <https://www.gnu.org/licenses/>.

.. _group_command_ref-label:

##############
 Group Command
##############

Synopsis
========

``dnf5 group <subcommand> [options] [<group-spec>...]``


Description
===========

The ``group`` command in ``DNF5`` offers several queries for getting information about groups, packages
related to them and it is also used for groups installation.

Optional ``group-spec`` arguments could be passed to filter only groups with given names.


Subcommands
===========

``list``
    List all matching groups, either among installed or available groups. If
    nothing is specified, list all known groups. ``--installed`` and ``--available``
    options narrow down the requested list. If ``--hidden`` option is used, also
    hidden groups are included in the list.

``info``
    Print detailed information about groups.
    The command accepts the same options as the ``list`` subcommand.

``install``
    Mark the specified groups installed and install packages it contains.
    Also include optional packages of the group if the ``--with-optional`` option is
    specified. All `Mandatory` and `Default` packages will be installed whenever
    possible. `Conditional` packages are installed if they meet their requirement.
    If the group is already (partially) installed, the command  installs the missing
    packages from the group.

    If the ``--no-packages`` option is used, no new packages will be installed by
    this command. Only currently installed group packages are considered to be installed
    with the group.

``remove``
    Mark the group removed and remove those packages in the group  from  the
    system  which  do not belong to another installed group and were not installed
    explicitly by the user.

    If the ``--no-packages`` option is used, no packages will be removed by this
    command.

Options
=======

``--available``
    | Show only available groups. Those which are not installed, but known to ``DNF5``.

``--installed``
    | Show only installed groups.

``--hidden``
    | Show also hidden groups.

``--with-optional``
    | Used with ``install`` command to include optional packages from the groups.

``--no-packages``
    | Used with ``install`` and ``remove`` commands to operate exclusively on the groups without manipulating any packages.

``--contains-pkgs``
    | Show only groups containing packages with specified names. List option, supports globs.

``--forcearch=<arch>``
    | Force the use of a specific architecture.
    | :ref:`See <forcearch_misc_ref-label>` :manpage:`dnf5-forcearch(7)` for more info.


Examples
========

``dnf5 group list --hidden``
    | Show list of all groups, including hidden ones.

``dnf5 group info *xfce*``
    | Show detailed info about all groups related to ``Xfce``.

``dnf5 group install mysql --with-optional``
    | Install the ``mysql`` group including optional packages.


See Also
========

    | :manpage:`dnf5-comps(7)`, :ref:`Comps groups and environments <comps_misc_ref-label>`
    | :manpage:`dnf5-specs(7)`, :ref:`Patterns specification <specs_misc_ref-label>`
