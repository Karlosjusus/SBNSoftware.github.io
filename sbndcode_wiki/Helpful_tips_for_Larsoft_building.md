---
lang: en
title: Helpful tips for Larsoft building
---

[]{#Helpful-tips-for-LArsoft}

Helpful tips for LArsoft[¶](#Helpful-tips-for-LArsoft){.wiki-anchor}
====================================================================

This is a combine list of things you might find useful when using
LArsoft. The examples are taken from other Redmine LArsoft sites:

1.  LArsoft: [Quick-start Guide to using and developing LArsoft
    code](https://cdcvs.fnal.gov/redmine/projects/larsoft/wiki/_Quick-start_guide_to_using_and_developing_LArSoft_code_){.external}

for more please see them. Please add to the list as well!

[]{#Updating-LArsoft-version-whilst-keeping-the-old-compilation}

Updating LArsoft version whilst keeping the old compilation[¶](#Updating-LArsoft-version-whilst-keeping-the-old-compilation){.wiki-anchor}
------------------------------------------------------------------------------------------------------------------------------------------

This is useful for when you want concurrent prof/debug builds using the
same source code or you want to update your LArsoft version. You can
keep you old build with the version of LArsoft you were running and test
if updating causes some error to appear. From a new shell setup the
LArsoft version you want e.g. if you wanted v06\_59\_00:

    setup larsoft v06_59_00 -q e14:prof
    cd v06_59_00.prof
    mrb newDev -T v06_59_00.prof -f

-T tells mrb what directory to put the localproducts and build directory
in.\
-f tells mrb to use the src directory that already exists.

[]{#Performing-a-Clean-Build}

Performing a Clean Build[¶](#Performing-a-Clean-Build){.wiki-anchor}
--------------------------------------------------------------------

The is stolen from site 1. Setup your code.\

    cd $MRB_BUILDDIR
    mrb z
    mrbsetenv 
    mrb i -j4  

The z is short for zapBuild and it removes all the local files out of
the local repository.

[]{#Removing-a-package-from-a-work-area-}

Removing a package from a work area .[¶](#Removing-a-package-from-a-work-area-){.wiki-anchor}
---------------------------------------------------------------------------------------------

This is stolen from site 1. Setup your code.

    cd $MRB_SOURCE
    rm -rf <repo-name>
    mrb uc 

[]{#Looking-at-the-builds-available}

Looking at the builds available[¶](#Looking-at-the-builds-available){.wiki-anchor}
----------------------------------------------------------------------------------

Do the following command to see what qualifiers and versions of sbndcode
are available.

    ups list -aK+ sbndcode 

[]{#Add-a-new-package-to-your-LArsoft-version}

Add a new package to your LArsoft version.[¶](#Add-a-new-package-to-your-LArsoft-version){.wiki-anchor}
-------------------------------------------------------------------------------------------------------

Setup your code. Find the version of the package you are downloading
your require via the LArsoft release website:
<https://cdcvs.fnal.gov/redmine/projects/larsoft/wiki/LArSoft_release_list>.
For example if you wanted the package that corresponded to v06\_59\_00
then:

    cd $MRB_SOURCE
    mrb g -t v06_59_00 package
    mrb z 
    mrb i -j4 
    mrbslp 