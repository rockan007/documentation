============
Pivot tables
============

Pivot tables - or simply pivots - are used to aggregate your records' data and break it down for
analysis. They are often available for reports found under the :guilabel:`Reporting` menu of most
apps but can be found in other places. Click the :guilabel:`Pivot` view button located at the top
right to access them.

.. image:: pivot/pivot-button.png
   :align: center
   :alt: Selecting the pivot view

.. _pivot/filters:

Filtering records
=================

Using a pivot involves ensuring the right records are selected. A default filter is set to select
relevant records when you open a pivot view. You can modify it by clicking :guilabel:`Filters`
and selecting one or several **pre-configured filtering options**.

.. example::
   On the :guilabel:`Sales Analysis` report, only records that are at the sales order stage are
   selected by default. However, you could *also* include records at the quotation stage by
   selecting :guilabel:`Quotations`. Furthermore, you could *only* include records from a specific
   year, for example 2022, by selecting :menuselection:`Order Date --> 2022`.

   .. image:: pivot/filters.png
      :align: center
      :alt: Example of a re-configured filter on the Sales Analysis report

.. _pivot/filters/custom:

Custom filters
--------------

From there, you can also create a custom filter using a wide selection of fields present on the
model by clicking :guilabel:`Add Custom Filter`, selecting a field, an operator, a value, and
clicking :guilabel:`Apply`.

.. example::
   You could *only* include records from a single salesperson, for example Mitchell Admin, by
   selecting :guilabel:`Salesperson` as the field, :guilabel:`is equal to` as the operator, and
   typing `Mitchell Admin` as the value.

   .. image:: pivot/custom-filter.png
      :align: center
      :alt: Example of a custom filter on the Sales Analysis report

.. note::
   If the records should *only* match one of several conditions, click :guilabel:`Add a condition`
   before applying a custom filter. If the records should match *all* conditions, add new
   custom filters instead.

.. _pivot/filters/search:

Search box
----------

You can also use the search box to quickly look for specific values and add them as a filter. Either
type the full value you are searching for and select the desired field, or type a part of the
value, click the dropdown button (:guilabel:`⏵`) before the desired field, and select the exact
value you are looking for.

.. example::
   Instead of adding a custom filter to select records where Mitchell Admin is the salesperson, you
   could search for `Mitch`, click the dropdown button (:guilabel:`⏵`) next to :guilabel:`Search
   Salesperson for: Mitch`, and select :guilabel:`Mitchell Admin`.

   .. image:: pivot/search-box.png
      :align: center
      :alt: Using the search box to find specific records on the Sales Analysis report

.. note::
   The search box is equivalent to using the *contains* operator when adding a custom filter. If you
   enter a partial value and directly select the desired field, all records containing the
   characters you typed will be filtered.

.. _pivot/measures:

Choosing measures
=================

Once the right records are filtered, you should choose what to measure. By default, a measure is
always selected. If you wish to edit it, click :guilabel:`Measures` and select one or multiple
fields. The different measures are then added as columns on the pivot.

.. example::
   You could add the :guilabel:`Margin` and :guilabel:`Count` measures to the Sales Analysis report,
   which only displays the :guilabel:`Untaxed Amount` by default.

   .. image:: pivot/measures.png
      :align: center
      :alt: Selecting different measures on the Sales Analysis report

.. note::
   When you select a measure, Odoo aggregates the values recorded on that field for the filtered
   records. Only numerical fields (:ref:`integer <studio/fields/simple-fields/integer>`,
   :ref:`decimal <studio/fields/simple-fields/decimal>`, :ref:`monetary
   <studio/fields/simple-fields/monetary>`) can be measured. In addition, the :guilabel:`Count`
   option is used to count the total number of filtered records.

.. _pivot/dimensions:

Grouping measures: dimensions
=============================

Grouping measures is useful for dividing data in smaller subsets for analysis. A typical dimension
is *Date > Month*, which is used to analyze the evolution of a measure over the months. To add a
dimension, click the plus button (:guilabel:`➕`) next to :guilabel:`Total` at the level of rows or
columns and select one of the **pre-configured dimensions**. To remove a dimension, click the minus
button (:guilabel:`➖`).

.. example::
   You could divide the measures by the :guilabel:`Product Category` dimension on the previous
   example's rows.

   .. image:: pivot/single-dimension.png
      :align: center
      :alt: Adding a dimension on the Sales Analysis report

.. tip::
   Click on a measure's label to sort the values by ascending (⏶) or descending (⏷) order.

You can also create a **custom dimension** using a wide selection of fields present on the model by
clicking the plus button (:guilabel:`➕`), selecting a field, and clicking :guilabel:`Apply`.

.. _pivot/dimensions/multiple:

Multiple dimensions
-------------------

Once you have added a dimension, you can add another one on the opposite axis or on a *single* of
the newly divided values.

.. example::
   You could further divide the measures by the :guilabel:`Salesperson` dimension on the previous
   example's columns and by the :guilabel:`Order Date > Month` dimension on the :guilabel:`All /
   Saleable / Office Furniture` product category.

   .. image:: pivot/multiple-dimensions.png
      :align: center
      :alt: Adding multiple dimensions on the Sales Analysis report

To add dimensions on the pivot’s rows quickly, you can use the :guilabel:`Group By` button below the
search box. If you have more than one dimension, the new dimension will be applied to *all* values
of the previous dimension.

.. tip::
   - Click the flip axis button (:guilabel:`⇄`) to switch the rows and columns' dimensions.
   - Download a `.xlsx` version of the pivot by clicking the download button (:guilabel:`⭳`).

.. _pivot/insert:

Inserting in a spreadsheet
==========================

When you have obtained the desired pivot, it is time to insert it in a spreadsheet. To do so, click
:guilabel:`Insert in spreadsheet`. In the pop-up box, rename the pivot if needed, and either create
a new spreadsheet by selecting :guilabel:`Blank spreadsheet` or insert it in an existing spreadsheet
by selecting it, then click :guilabel:`Confirm`.

.. image:: pivot/insert-spreadsheet.png
   :align: center
   :alt: Inserting a pivot in a spreadsheet

.. note::
   By default, new spreadsheets are saved under the :guilabel:`Spreadsheet` workspace of the
   Documents app.

.. _pivot/insert/link:

Data link
---------

A pivot's measures are kept updated, reflecting any changes made to your database. The measures are
re-loaded every time you open a spreadsheet. To update them directly from the spreadsheet, go to
:menuselection:`Top bar: Data --> Refresh all data`.

.. note::
   If new values have been added to a dimension, you need to go to :menuselection:`Top bar:
   Data --> Re-insert pivot` to insert the new values. Alternatively, go to :menuselection:`Top bar:
   Data --> Insert pivot`, select the pivot, and tick :guilabel:`Display missing cells only` to
   preview first which values would be added.

   .. image:: pivot/missing-cells.png
      :align: center
      :alt: Adding multiple dimensions on the Sales Analysis report

.. _pivot/insert/properties:

Edit pivot properties
---------------------

To edit a pivot's properties, right-click on one of its cells, and select :guilabel:`See pivot
properties`. You can:

- :guilabel:`Rename` it.
- Use :guilabel:`Edit domain` to change which records are :ref:`selected <pivot/filters>`.
- :guilabel:`Delete` it.
- View its properties (which model, dimensions, measures, etc.).

.. tip::
   You can manually add pivot measures by using the `=ODOO.PIVOT` formula and headers by using
   `=ODOO.PIVOT.HEADER`.
