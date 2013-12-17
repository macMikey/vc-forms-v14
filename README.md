# VC_Forms v14

## READ THIS FIRST!

This component is not ready for primetime. Only use it if you are willing to deal with major bugs and possibly the need to start over from scratch. It has the bare minimum functionality (the ability to export the forms, the ability to export only the changed forms).

Also, 4D v14 is REQUIRED. VC_Forms relies on new commands in v14.

## Description

The VC_Forms component facilitates automatic export of all forms in a [4D](http://www.4d.com) host database to text files on disk.  The forms are exported as JSON.  If the host database is under revision control, these text files are suitable for committing to the repository, thus giving the developer to ability to track changes to forms over time. Most importantly, the VC_Forms component is designed to have minimal impact on the host database.

The VC_Forms component can be extended to support revision control (RC) integration. If the host database (or another component) contains the following shared methods

* VC_DEVHOOK_Create
* VC_DEVHOOK_Update
* VC_DEVHOOK_Delete

The VC_Forms component will call these methods prior to saving/deleting the method. The callee can choose whether or not to allow the save as well as take any action necessary to notify the RC software of the change.

## Contents

* The [Components](https://github.com/4D/vc-forms-v14/tree/master/Components) folder contains the "VC_Forms.4dbase" component suitable for installation in any [4D v14](http://www.4d.com/products/4dv14.html) database.
* The [matrix](https://github.com/4D/vc-forms-v14/tree/master/matrix) folder contains the component source code.

## Usage

It is HIGHLY recommended that you already have [VC_Framework v14](https://github.com/4D/vc-framework-v14) installed and activated prior to installing VC_Forms.  VC_Forms can technically be used on its own but this ability isn't fully implemented yet.

Install the component (do NOT install an alias, you must install the component), launch the host database in 4D, and open a method if none are open. This will launch the stored procedure to manage form export.

Alternatively there is a macro included to install startup code so that the process can be automatically launched (e.g. via "On Startup").

Note: the first export may take some time in larger databases.

If you modify the matrix database, you should build a new component.  To build a new component, execute the BLD_Build method from the matrix database (the matrix database uses the ["BLD.4dbase" component](https://github.com/4D/interpreted-build-v14)).
