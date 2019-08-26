py-Glances-pkgsrc
==========

NetBSD pkgsrc script for script for `py-Glances`.

You can find `Glances` [here][1]

NOTE: This package is not yet available in the pkgsrc tree.

Installation
------------

Copy `sysutils/py-Glances` folder to `/usr/pkgsrc` directory.

NOTE: If your pkgsrc directory is different from above, copy to the respective
place.

Usage
-----

Once you have copied the folder, install it as you would do for any port.

`$ cd /usr/pkgsrc/sysutils/py-Glances`<br>
`$ make install clean`

For a list of dependencies for the build check [here][2]

NOTE: If you are using pkgsrc in a non NetBSD system, replace `make` with
`bmake` in the above example.

Credits
-------

* `Glances` is developed and maintained by the [Nicolas Hennion][3]

License
-------

BSD 2-clause. See LICENSE.

[1]: https://nicolargo.github.io/glances/
[2]: https://github.com/nicolargo/glances#requirements
[3]: https://sourcerer.io/nicolargo
