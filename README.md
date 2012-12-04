= webinos policy editor =

==- Context list:

The ‘context’ entries in the list in AllowDenyPolicyEditor_XXX are effectively workable subsets of a policy.  The idea is that we could, if we wish, extend this definition to be subsets of the policy specific to devices in a personal zone as well.  However, it would be useful to prototype and evaluate this UI before figuring out whether the extension is useful or not.
There isn’t a toolbar button for adding these, but the idea is that the user would right click in this list and speed menu would appear giving the option to ‘add’ or ‘delete’ a context.

In implementation terms, the idea is that each ‘context’ entry will correspond to an individual XACML policy set file.  In theory, the entries in these files shouldn’t conflict, however the editor will check for conflicts.  For example “Current destination” might be allowed in one context, but “Final destination” might be denied in another. In both cases, the field may refer to ‘Destination’ in the ‘Kids in Focus’ application

==  Allow/Deny palette:

The palette is situated around the user model that non-security users have around security policies in that data items are explicitly allowed or denied.  The expectation will be that anything that isn’t visible in the policy will be prompted.  When a policy prompt is received outside of the editor and the user responds with something like ‘always allow’ or ‘always deny’ then the object will be added to the allow / deny entry in the ‘Misc’ context.  A user can, they wish, then cut objects from this context and paste them into another to help organise/categorise these objects.  Again, when we’ve got a working prototype, it will be interesting to see if people actually do this or not.

== Category dialog (NavigationAllowCategory):

The Allow/Deny palette supports hit-testing.  For example, if you highlight ‘trip to dad’s’ and click on the Navigation category then the NavigationAllowCategory UI pops up.  “Categories” group objects that will be subject to access control.  Rectangles refer to data, and parallelogram’s refer to device services.  These are created by clicking on the Add button in the AllowDenyPolicyEditor_XXX.bmml interface and selecting “Category” (not shown)

== Objects and Device Services dialog (NavigationAllowCategory, CurrentDestinationAllow):

If you click on either “Current destination” or “GPS” in NavigationAllowCategory then this UI should pop up.

I’m assuming that the widget manifest will indicate what items of data are potentially shareable across personal zones, as well as what device services are in use.   Each object or device service will have a user specified name, i.e. “Current Destination”/“GPS”, an application the object/service is related to, a ‘field’ or ‘device service’ (again - specified in the widget manifest), and an action.  

== Other toolbar buttons:

* Open / Save: These open and save a collection of XACML files corresponding to the ‘context’ entries respectively
* Test: This will entail carrying some sort of validation of the policy.  I haven’t mocked this up yet, but I’ve got 2 possibilities in mind here:
(a) Grid with objects/service rows, personal zone columns, and green/red/amber cells depending on the action associated with this.
(b) Some sort of interactive quiz where the user might be tested on what the access control settings for different things in their policy might be.  
Incidentally, these tests work across ALL contexts, not just a specific entry.
* Synchronise: Uploads policies for distribution to all devices across a personal zone.  I haven’t mocked up the dialog for this just yet
* Add / Delete:  Adds/Deletes objects and categories as above. For the delete to work, an object or category needs to be selected.
* Zoom: This will zoom out/in the allow/deny palette.

== Conflict checking

In implementation terms, the idea is that each ‘context’ entry will correspond to an individual XACML policy set file.  In theory, the entries in these files shouldn’t conflict, however the editor will check for conflicts.  For example “Current destination” might be allowed in one context, but “Final destination” might be denied in another. In both cases, the field may refer to ‘Destination’ in the ‘Kids in Focus’ application
