<strong>Holding Updates to Packages</strong>

Updating your system is really important. There are new security vulnerabilities found all the time, even in Linux. This means that keeping your operating system and its packages up to date is part of keeping you secure and safe from any online threats. Or any other threat for that matter.

However, there may be times when you may need to hold a package from being updated. In most package managers, such as apt, this can be accomplished quite easily. Every single package manager has this ability if I am not mistaken so learning how to use it on all of the package managers you may have on your system would be very helpful.

Some of the reasons why you may need to hold a package from being updated is that the most current version conflicts with other packages that you have on your system. Or you are developing some software or tools that require a particular version of a package and you don't want to risk breaking your code by updating to the latest version.

To hold a package from being updated you would simply use the following command:
```
    sudo apt-mark hold [packagename]
```

To show all packages that have been on hold you would use the following:
```
    sudo apt-mark showhold
```

To remove a hold on a package you would use the following command:
```
    sudo apt-mark unhold [packagename]
```

Finally, you may want to show all packages that are upgradeable that you have installed on your system. To do this you would simply use the following command:
```
    sudo apt list --upgradable
```

This should give you an idea on how to hold packages back using the apt package manager. Each package manager has their own methods of doing this so please either refer to those lectures or just search how to do that on the Internet. This tutorial was just covering the apt package manager.

