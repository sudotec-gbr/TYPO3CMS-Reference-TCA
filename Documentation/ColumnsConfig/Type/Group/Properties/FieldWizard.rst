.. include:: /Includes.rst.txt
.. _group-fieldWizard:

===========
fieldWizard
===========

For general fieldWizard documentation see :ref:`here <tca_property_fieldWizard>`.

.. _tca_property_fieldWizard_recordsOverview:

.. confval:: recordsOverview

   :Path: $GLOBALS['TCA'][$table]['columns'][$field]['config']['fieldWizard']
   :type: array
   :Scope: fieldWizard

   Render an overview of the selected records with correct icon and click menu and title. Allows to
   perform actions on the selected records directly. Links the record title to a direct editing form.

.. _tca_property_fieldWizard_tableList:

.. confval:: tableList

   :Path: $GLOBALS['TCA'][$table]['columns'][$field]['config']['fieldWizard']
   :type: array
   :Scope: fieldWizard

   Render a list of allowed tables and link to element browser. This field wizard is enabled by default.
   This wizard allows to easily select records from a popup.
