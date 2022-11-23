.. _howto/jstraining/01_components:

=====================
Chapter 1: Components
=====================

This chapter introduces the `Owl framework <https://github.com/odoo/owl>`_, a tailor-made component
system for Odoo. The main building blocks of OWL are `components
<https://github.com/odoo/owl/blob/master/doc/reference/component.md>`_ and `templates
<https://github.com/odoo/owl/blob/master/doc/reference/templates.md>`_.

In Owl, every part of user interface is managed by a component: they hold the logic and define the
templates that are used to render the user interface. In practice, a component is represented by a
small JavaScript class subclassing the `Component` class.

.. example::
   The `Counter` class implements a component that holds the internal state of a counter and defines
   how it should be incremented.

   .. code-block:: js

      const { Component, useState } = owl;

       class Counter extends Component {
           static template = "my_module.Counter";

           state = useState({ value: 0 });

           increment() {
               this.state.value++;
           }
       }

   The `Counter` class specifies the name of the template to render. The template is written in XML
   and defines a part of user interface.

   .. code-block:: xml

       <templates xml:space="preserve">
           <t t-name="my_module.Counter" owl="1">
               <p>Counter: <t t-esc="state.value"/></p>
               <button class="btn btn-primary" t-on-click="increment">Increment</button>
           </t>
       </templates>

Let us take some time to get used to Owl itself. Below, you will find a series of exercises intended
to quickly understand and practice the basics of Owl.

Here is an overview of what we are going to achieve in this chapter:

.. todo:: update screenshot

.. image:: 01_components/overview.png
   :scale: 120%
   :align: center
   :alt: Overview of chapter 1.

Displaying a counter
====================

As a first exercise, let us implement a counter in the `Playground` component located in
:file:`owl_playground/static/src/`.

.. exercise::
   #. Modify :file:`playground.js` so that there is a counter variable in the `setup`. You will need
      to use the `useState
      <https://github.com/odoo/owl/blob/master/doc/reference/hooks.md#usestate>`_ function so that
      the component is re-rendered whenever any part of the state object has been read by this
      component is modified.
   #. In the same component, create an `increment` method.
   #. Modify the template in :file:`playground.xml` so that it displays your counter variable. Use
      `t-ecs <https://github.com/odoo/owl/blob/master/doc/reference/templates.md#outputting-data>`_
      to output the data.
   #. Add a button in the template and specify a `t-on-click
      <https://github.com/odoo/owl/blob/master/doc/reference/event_handling.md#event-handling>`_
      attribute in the button to trigger the `increment` method whenever the button is clicked.

   .. image:: 01_components/counter.png
      :align: center
      :alt: A counter component.

.. spoiler:: Solution

   todo

Extract counter in a component
==============================

For now we have the logic of a counter in `Playground`, let us see how to create a sub component
from it.

- Extract the counter code from the ``Playground`` component into a new ``Counter`` component.
- You can do it in the same file first, but once it's done, update your code to move the ``Counter``
  in its own file.
- Make sure the template is in its own file, with the same name.

.. warning:: Don't forget the ``/** @odoo-module **/`` in your javascript files, more information
             on this can be found :ref:`here <frontend/modules/native_js>`.

A todo component
================

We will create new components in ``owl_playground/static/src/`` to keep
track of a list of todos. This will be done incrementally in multiple exercises, that will
introduce various concepts.


First, let's create a ``Todo`` component that display a task, which is described by an
id (number), a description (string) and a status done (boolean). For example:

    .. code-block:: javascript

        { id: 3, description: "buy milk", done: false }

- Create a ``Todo`` component that receive a ``todo`` in
  `props <https://github.com/odoo/owl/blob/master/doc/reference/props.md>`_, and display it:
  it should show something like ``3. buy milk``
- Add the bootstrap classes ``text-muted`` and ``text-decoration-line-through`` on the task
  if it is done
- modify ``owl_playground/static/src/playground.js`` and ``owl_playground/static/src/playground.xml``
  to display your new ``Todo`` component, with some hardcoded props to test it first. For example

    .. code-block:: javascript

        setup() {
            ...
            this.todo = { id: 3, description: "buy milk", done: false };
        }

.. note:: References:

    - `owl: props <https://github.com/odoo/owl/blob/master/doc/reference/props.md>`_
    - `owl: Dynamic attributes <https://github.com/odoo/owl/blob/master/doc/reference/templates.md#dynamic-attributes>`_
    - `owl: Dynamic class attributes <https://github.com/odoo/owl/blob/master/doc/reference/templates.md#dynamic-class-attribute>`_

.. spoiler:: Preview

    .. image:: 01_components/todo.png
       :align: center
       :alt: A Todo component


.. spoiler:: Solution

    - `Solution of the exercice can be found here (TODO) <https://github.com/ged-odoo/odoo-js-training-public/commit/efd7bdbf6f12abd44479de6de5ae96525649d925>`_

Props validation
================

The Todo component has an implicit API: it expects to receive in its props the description of a
todo in a specified format: `id`, `description` and `done`. Let us make that API more explicit:
we can add a props definition that will let Owl perform a validation step in dev mode.
It is a good practice to do that for every component.

- Add `props validation <https://github.com/odoo/owl/blob/master/doc/reference/props.md#props-validation>`_ to ``Todo``
- Make sure it fails in dev mode

.. note:: References:

    - `owl: props validation <https://github.com/odoo/owl/blob/master/doc/reference/props.md#props-validation>`_
    - :ref:`odoo: debug mode <frontend/framework/debug_mode>`
    - :ref:`odoo: activate debug mode <developer-mode>`

.. spoiler:: Solution

    - `Solution of the exercice can be found here (TODO) <https://github.com/ged-odoo/odoo-js-training-public/commit/efd7bdbf6f12abd44479de6de5ae96525649d925>`_

A list of todos
===============

Now, let us display a list of todos instead of just one todo. For now, we can
still hardcode the list.

- Change the code to display a list of todos, instead of just one, and use
  `t-foreach` in the template
- Think about how it should be keyed

.. note:: References:

    - `owl: t-foreach <https://github.com/odoo/owl/blob/master/doc/reference/templates.md#loops>`_

.. spoiler:: Preview

    .. image:: 01_components/todoList.png
       :align: center
       :alt: A TodoList


.. spoiler:: Solution

    - `Solution of the exercice can be found here (TODO) <https://github.com/ged-odoo/odoo-js-training-public/commit/efd7bdbf6f12abd44479de6de5ae96525649d925>`_

Adding a todo
=============

So far, the todos in our list are hardcoded. Let us make it more useful by allowing the user to add
a todo to the list.

- Add input above the task list with placeholder ``Enter a new task``
- Add an event handler on the ``keyup`` event named ``addTodo``
- Implement ``addTodo`` to check if enter was pressed (``ev.keyCode === 13``), and
  in that case, create a new todo with the current content of the input as description
- Make sure it has a unique id (it can be just a counter that increments at each todo)
- Then clear the input of all content
- Bonus point: don't do anything if input is empty

Notice that nothing updates in the UI: this is because Owl does not know that it
should update the UI. This can be fixed by wrapping the todo list in a `useState`

.. code-block:: javascript

    this.todos = useState([]);

.. note:: References:

    - `owl: reactivity <https://github.com/odoo/owl/blob/master/doc/reference/reactivity.md>`_
    - `owl: event handling <https://github.com/odoo/owl/blob/master/doc/reference/event_handling.md>`_

.. spoiler:: Preview

    .. image:: 01_components/createTodo.png
       :align: center
       :alt: Creating todos

.. spoiler:: Solution

    - `Solution of the exercice can be found here (TODO) <https://github.com/ged-odoo/odoo-js-training-public/commit/efd7bdbf6f12abd44479de6de5ae96525649d925>`_

Focusing the input
==================

Let's see how we can access the DOM with `t-ref <https://github.com/odoo/owl/blob/master/doc/reference/refs.md>`_.

- Focus the ``input`` from the previous exercise whenever the dashboard is mounted.
- Bonus point: extract the code into a specialized hook ``useAutofocus``

.. note:: References:

    - `owl: component lifecycle <https://github.com/odoo/owl/blob/master/doc/reference/component.md#lifecycle>`_
    - `owl: hooks <https://github.com/odoo/owl/blob/master/doc/reference/hooks.md>`_
    - `owl: useRef <https://github.com/odoo/owl/blob/master/doc/reference/hooks.md#useref>`_

.. spoiler:: Solution

    - `Solution of the exercice can be found here (TODO) <https://github.com/ged-odoo/odoo-js-training-public/commit/efd7bdbf6f12abd44479de6de5ae96525649d925>`_


Toggling todos
==============

Now, let's add a new feature: mark a todo as completed. This is actually
trickier than one might think: the owner of the state is not the same as the
component that displays it. So, the `Todo` component need to communicate to its
parent that the todo state needs to be toggled. One classic way to do this is
by using a callback prop `toggleState`

- Add an input of ``type="checkbox"`` before the id of the task, which is checked if
  the ``done`` state is true
- Add a callback props ``toggleState``
- Add a ``click`` event handler on the input in ``Todo``, and make sure it calls
  the `toggleState` function with the todo id.
- Make it work!

.. note:: References:

    - `owl: binding function props <https://github.com/odoo/owl/blob/master/doc/reference/props.md#binding-function-props>`_

.. spoiler:: Preview

    .. image:: 01_components/togglingTodo.png
       :align: center
       :alt: Toggling todos

.. spoiler:: Solution

    - `Solution of the exercice can be found here (TODO) <https://github.com/ged-odoo/odoo-js-training-public/commit/efd7bdbf6f12abd44479de6de5ae96525649d925>`_

Deleting todos
==============

The final touch is to let the user delete a todo.

- Add a new callback prop ``removeTodo``
- Add a ``<span class="fa fa-remove">`` in the Todo component
- Ahenever the user clicks on it, it should call the ``removeTodo`` method
- Make it work as expected

.. spoiler:: Preview

    .. image:: 01_components/deletingTodo.png
       :align: center
       :alt: Deleting todos

.. spoiler:: Solution

    - `Solution of the exercice can be found here (TODO) <https://github.com/ged-odoo/odoo-js-training-public/commit/efd7bdbf6f12abd44479de6de5ae96525649d925>`_

Generic components with slots
=============================

Owl has a powerful slot system to allow you to write generic components. This is
useful to factorize common layout between different parts of the interface.


- Write a ``Card`` component, using the following bootstrap html structure:

    .. code-block:: html

        <div class="card" style="width: 18rem;">
            <img src="..." class="card-img-top" alt="..." />
            <div class="card-body">
            <h5 class="card-title">Card title</h5>
            <p class="card-text">
                Some quick example text to build on the card title and make up the bulk
                of the card's content.
            </p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
            </div>
        </div>

- This component should have two slots: one slot for the title, and one for
  the content (the default slot). For example, here is how one could use it:

    .. code-block:: html

        <Card>
            <t t-set-slot="title">Card title</t>
            <p class="card-text">Some quick example text...</p>
            <a href="#" class="btn btn-primary">Go somewhere</a>
        </Card>

- Bonus point: if the ``title`` slot is not given, the ``h5`` should not be
  rendered at all

.. note:: References:

    - `owl: slots <https://github.com/odoo/owl/blob/master/doc/reference/slots.md>`_
    - `owl: slot props <https://github.com/odoo/owl/blob/master/doc/reference/slots.md#slots-and-props>`_
    - `bootstrap: documentation on cards <https://getbootstrap.com/docs/5.2/components/card/>`_

.. spoiler:: Preview

    .. image:: 01_components/card.png
       :align: center
       :alt: Creating card with slots

.. spoiler:: Solution

    - `Solution of the exercice can be found here (TODO) <https://github.com/ged-odoo/odoo-js-training-public/commit/efd7bdbf6f12abd44479de6de5ae96525649d925>`_

Miscellaneous small tasks
=========================

- Add prop validation on the ``Card`` component
- Try to express in the prop validation system that it requires a ``default``
  slot, and an optional ``title`` slot

.. note:: References:

    - `owl: props validation <https://github.com/odoo/owl/blob/master/doc/reference/props.md#props-validation>`_
