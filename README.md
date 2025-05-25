# Knotscape 1.01

[![Build](https://github.com/aziis98/knotscap/actions/workflows/build.yml/badge.svg)](https://github.com/aziis98/knotscap/actions/workflows/build.yml)

## Fork Notes

-   This is still very unstable but somewhat works if we ignore some random
    error boxes that sometimes pop up when resizing the window.

-   Some actions like "Draw Knot" for some reason don't work or hang for now.

## Usage

To run Knotscape, you need to have Tcl/Tk installed on your system. Then you can
build and run it with the following commands:

```bash
$ https://github.com/aziis98/knotscap
$ make
$ ./knotscape
```

## Project Structure

Knotscape is primarily a Tcl/Tk application that provides a graphical user
interface for exploring knot theory concepts. Its structure can be understood at
a high level as follows:

-   **Main Application (`knotscape` script & `tcl/` directory):**

    -   The `knotscape` shell script is the main entry point, which launches the
        Tcl/Tk-based GUI.

    -   The `tcl/` directory contains numerous Tcl scripts (`.tcl` files). These
        scripts define the user interface elements, event handling, and the core
        logic of the application. They are organized into various procedures
        (Tcl `proc`s) that manage different functionalities like displaying
        knots, handling user input, and orchestrating calls to backend programs.

-   **Computational Backend (C Programs in `src/`):**

    -   Knotscape offloads computationally intensive tasks to a suite of
        external programs written in C. The source code for these programs
        resides in the `src/` directory.

    -   Upon compilation (using the `Makefile`), these C programs are placed as
        executables in the `bin/` directory.

    -   Examples of such programs include:

        -   `poly1` and `poly2`: Used for computing various knot polynomials.

        -   `draw`: Handles the generation of knot diagrams.

        -   `knotfind`, `locate_a`, `locate_n`: Used for searching and
            identifying knots in the database.

        -   Other specialized programs for tasks like calculating hyperbolic
            invariants, checking knot properties, etc.

-   **Data and Resources:**

    -   `knotTable/`: Contains the database of knots.

    -   `doc/`: Provides documentation, including conversion tables for knot
        notations.

    -   `help/`: Stores help files accessible from the application.

    -   `gif/`: Contains images used in the GUI.

    -   `lib/`: Includes auxiliary data files used by some of the backend
        programs.

This separation allows the Tcl/Tk frontend to remain responsive while the C
programs perform complex calculations.

## Help Outline

The `help/` directory contains plain text files that provide guidance on various
aspects of Knotscape. The [`help/help.toc`](help/help.toc) file serves as a
table of contents for these help files. Here's a brief overview of the key help
topics:

-   **[`help.tutorial`](help/help.tutorial)**: A step-by-step guide for new
    users to learn the basics of Knotscape.

-   **[`help.notation`](help/help.notation)**: Explains the different systems of
    notation used to describe knots within the program (e.g.,
    Dowker-Thistlethwaite, Alexander-Briggs).

-   **[`help.enter`](help/help.enter)**: Instructions on how to manually input
    knots into the application, typically using a specific notation.

-   **[`help.linksmith`](help/help.linksmith)**: Detailed guide on using
    LinkSmith, the graphical tool for drawing and editing knot and link diagrams
    with the mouse.

-   **[`help.locate`](help/help.locate)**: How to search for and identify knots
    within Knotscape's extensive database.

-   **[`help.draw`](help/help.draw)**: Information on generating and customizing
    visual diagrams of knots.

-   **[`help.hyperbolic`](help/help.hyperbolic)**: Covers the calculation and
    interpretation of hyperbolic invariants for knots, a key feature for
    studying knot geometry.

-   **[`help.polynomials`](help/help.polynomials)**: Describes the various knot
    polynomials (e.g., Alexander, Jones, HOMFLY) that Knotscape can compute and
    their significance.

-   **[`help.homomorphisms`](help/help.homomorphisms)**: Details on working with
    representations of knot groups and their homomorphisms.

-   **[`help.shortcuts`](help/help.shortcuts)**: A list of keyboard shortcuts to
    speed up common operations.

-   **[`help.limits`](help/help.limits)**: Outlines the operational boundaries
    of the software, such as the maximum number of crossings it can handle.

-   **[`help.editing`](help/help.editing)**: Provides tips and instructions for
    text editing within Knotscape's various windows and input fields.

---

4-1-99 by Jim Hoste and Morwen Thistlethwaite, with help from Bruce Ewing, Ken
Millett, Ken Stephenson and Jeff Weeks.

## Features added since Version 1.0:

1.  LinkSmith has a new "Export" menu, with two options:

    1.  save the current link diagram in Ewing-Millett format;

    2.  save the underlying link complement as an ideal triangulation, in
        SnapPea-readable format.

2.  The horoball and drawing windows now have an option invoking a file-save
    dialogue box for saving the picture as a PostScript file.

3.  Hyperbolic invariants now occupy a separate (tear-off) submenu of the Action
    menu. There are two new features:

    1.  "Save Triangulation", which produces an ideal triangulation of the
        (hyperbolic) knot complement, and writes it to a file in
        SnapPea-readable format;
    2.  "Canonical Cell Decomposition", which displays the canonical cell
        decomposition of the knot complement, as viewed from the cusp. The
        canonical cell decomposition can be saved as a PostScript file. It is a
        complete invariant of cusped hyperbolic manifolds. For further details,
        see the Help file on hyperbolic invariants.

Some bug fixes are listed in the file FIXES.

## README for Version 1.0

Please see the file Credits.ps for details on contributors to Knotscape.

This version is an upgrade to Knotscape 1.0-BETA.

The main enhancement is the incorporation of LinkSmith, a program enabling the
user to draw a knot with a mouse. Also, Knotscape now includes in its database
all knots up to 16 crossings. Various other minor improvements have been made
since the beta version.

The original purpose of Knotscape was to provide convenient access to tables of
knots. Its purpose has expanded somewhat, particularly with the inclusion of the
hyperbolic invariants. The binaries which calculate hyperbolic invariants were
compiled against SnapPea 2.0; we are very grateful to Jeff Weeks, the author of
SnapPea, for making this possible. We'd like to emphasize that we take full
responsibility for any bugs that there might be in the hyperbolic part of
Knotscape.

At present, Knotscape will deal with knots up to 49 crossings. A database
containing all prime knots of up to 16 crossings is included. Dictionaries are
included in the doc directory for converting between classical numbering of
knots and Dowker-Thistlethwaite numbering. The doc directory also has a
subdirectory "symmetric_knots" containing all highly symmetric knots up to 16
crossings. These can be loaded into Knotscape and investigated.

The program requires Tcl 7.4, 7.5, 7.6 or 8.0 / Tk 4.0, 4.1 4.2 or 8.0.

Binaries of the executables are provided for the following two platforms:

i386 linux sunos

Source code is also provided in each version for all but one of the executables.

The procedures not dependant on SnapPea can be compiled in a straightforward
manner, using the Makefile in Knotscape's home directory. But we have not yet
tested Knotscape on any platform except those listed above, so it is likely that
there would be problems.

The program knotscape_hyp.c can also be compiled against Snappea-2.0,
downloadable from Jeff Weeks's home page at http://thames.northnet.org/weeks/ .
knotscape_hyp.c provides all the SnapPea functions in Knotscape except for the
computation of fixed point sets of symmetries, and the computation of the
canonical dell decomposition. The program knotscape_hyp.c refers to procedures
in decode_new_DT.c, also in the src directory.

The source code for computation of fixed point sets and the canonical
decomposition is not yet supplied, as the two programs in question have to be
compiled against non-standard versions of the SnapPea kernel. Hopefully these
will also be available in the near future.

We welcome any suggestions for improvements, and also of course reports of bugs.

Jim Hoste <jhoste@calvin.pitzer.edu> Morwen Thistlethwaite <morwen@math.utk.edu>

## Installation.

1.  Download the file `knotscape-1.0.<platform>.tar.gz`, where `<platform>` is
    appropriate for your computer, and copy to the directory where you wish
    Knotscape to be installed.

2.  Untar by typing `tar zxvf knotscape-1.0.<platform>.tar.gz`. On some systems
    the file has to be decompressed with gunzip before untarring with "tar xvf
    ... " A new directory "knotscape" will appear.

3.  Change directory to the new directory "knotscape".

4.  If necessary edit the shell script, also called "knotscape", to suit your
    system. The environment variable KSHOME should be set to the present
    directory. You may want to choose a different temporary directory from
    $KSHOME/tmp . This temporary directory is a scratch directory containing all
    the input and output files generated by the executables. It also contains
    any PostScript files generated by Knotscape. On some systems the command
    "wish" needs to be made more specific, as several different versions of Tk
    might be installed. Knotscape will not run on any version of Tk prior to
    4.0. Finally, ensure that all files have the correct permissions.

5.  Run Knotscape by typing "./knotscape", or simply "knotscape" if the current
    working directory is in your PATH variable.

## Getting started.

The easiest way of getting started is to use the browser window to enter one or
more knots in the input window. A tutorial can be accessed by clicking on "HELP"
followed by "Tutorial".

It's possible that machines with no swap partition or machines with a small
amount of memory will produce a segmentation violation when some of Knotscape's
options are invoked. If you are using a Linux machine, the solution is to create
a suitably large swap partition.
