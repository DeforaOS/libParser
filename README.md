DeforaOS libParser
==================

About libParser
---------------

libParser aims at providing parsers for common file formats, such as XML.


Dependencies for libParser
--------------------------

libParser depends on the following software components:
- pkg-config from the freedesktop software collection, as found in most
  software distributions already; otherwise at
  <http://www.freedesktop.org/wiki/Software/pkg-config/>
- libSystem from the DeforaOS Project, as found at
  <http://www.defora.org/os/project/27/libSystem> if not packaged for your
  system.
- configure from the DeforaOS Project, likewise found at
  <http://www.defora.org/os/project/16/configure>


Compiling libParser
---------------------

It is then possible to build the project with `make(1)` as usual. The following
command should therefore be enough:

    $ make

To install libParser in a dedicated directory, like `/path/to/libParser`:

    $ make PREFIX="/path/to/libParser" install
