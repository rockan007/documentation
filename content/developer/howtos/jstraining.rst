:show-content:

.. _howto/jstraining:

=====================================
Working with the javascript framework
=====================================

For this training, we will step into the shoes of the IT staff at the fictional company
Awesome T-Shirt, which is dedicated to printing custom t-shirts for online customers.
The Awesome T-Shirt company uses Odoo to manage orders and has created a dedicated Odoo module to
manage their workflow. The project is currently a simple kanban view, with a few columns.

The usual process is as follows: a customer looking for a nice t-shirt can simply order it from the
Awesome T-Shirt site and give the url for any image they want. They must also fill in some
basic information, such as the desired size and quantity of t-shirts. Once they have confirmed their order,
and once the payment has been validated, the system will create a task in our application.

The big bos of Awesome T-shirt, Bafien Carpink, is unhappy with our implementation.
He believes that by micromanaging more, he will be able to get more revenue from his employees.
As the IT staff for Awesome T-shirt, we are responsible with improving the system. Various independent tasks must be performed.

Let us now practice our Odoo skills!

.. _howtos/jstraining/setup:

Setup
=============

To follow the training, it is necessary to have a recent version of Odoo installed.
If you have not installed it yet, we recommend installing it from :ref:`source <setup/install/source>`
(:dfn:`running Odoo from source code`).

.. warning:: Be sure to follow the training on version 16.0 minimum. Odoo 16 is the start of a (mostly)
     brand new JavaScript codebase; taking the course in an older version may cause bugs or not work at all.

To setup your development environment, you can also follow the dedicated chapter in
:doc:`Getting Started: Development environment setup <rdtraining/02_setup>` tutorial.

The last things to do are:

- Clone the `JS Training respository <https://github.com/ged-odoo/odoo-js-training-public>`_.
- Add the modules to your addons path.
- Prepare a new database with awesome_tshirt installed.

You are now ready to take the training. Let's get started!

Exercises
=============

.. toctree::
    :caption: JS Training
    :titlesonly:
    :glob:

    jstraining/*

* :doc:`jstraining/01_owl_framework`
* :doc:`jstraining/02_odoo_web_framework`
* :doc:`jstraining/03_fields_and_views`
* :doc:`jstraining/04_miscellaneous`
* :doc:`jstraining/05_custom_kanban_view`
* :doc:`jstraining/06_creating_view_from_scratch`
* :doc:`jstraining/07_testing`

