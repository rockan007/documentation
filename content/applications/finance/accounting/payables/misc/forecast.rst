============================
Forecast future bills to pay
============================

In Odoo you have the possibility to manage payments by setting automatic **Payments Terms**
and **follow-ups**.

Configuration: payment terms
============================

In order to track the vendor conditions, we use **Payment Terms** in Odoo.
**Payment terms** allow keeping track of due dates on invoices. Examples of **Payment Terms** are:

-  50% within 30 days
-  50% within 45 days

To create **Payment terms**, use the :menuselection:`Accounting app --> Configuration -->
Invoicing --> Payment Terms`. By clicking on :guilabel:`Create`, you can add the terms you need as
well as modify existing ones by clicking on it in the Payment Terms list in the same view.

.. seealso::
   - `Odoo Tutorials: Payment terms <https://www.odoo.com/slides/slide/payment-terms-1679?fullscreen=1>`_

Once **Payment Terms** are defined, you can assign them to your vendor by default.
To do so go to :menuselection:`Vendors --> Vendors`, choose the :guilabel:`Vendor` you want and in
the :guilabel:`Sales & Purchase` tab you can select a specific **Payment Term**.
This way, every time you will purchase from this vendor, Odoo will automatically propose the chosen
payment term.

.. note::
   If you do not set a specific payment term on a vendor, you will still be able to set a specific
   payment term on the vendor bill.

Forecast bills to pay with the Aged Payable report
===================================================

In order to track amounts to be paid to the vendors, use the **Aged Payable** report. To get it,
click :menuselection:`Accounting app --> Reporting --> Partner Reports --> Aged Payable`. This
report gives you a summary per vendor of the amounts to pay, compared to their due date (the due
date being computed on each bill using the terms). This report tells you how much you will have to
pay within the following months.

Select bills to pay
===================

Using the menu :menuselection:`Vendors --> Bills`, you can get a list of vendor bills. Using the
filters, you can list all the bills to pay or that are overdue.

From this screen, you can also switch to the pivot table or the graph view to get statistics on the
amount due over the next month, using the group by "Due Date" feature.
