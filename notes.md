
# selection mode

In selection mode the + (add) button switches to the +cart (+bench) icon which means "add to bench".

## desktop

Enter selection mode by either selecting multiples using shift or control, or starting to drag a single item.

* changes the top bar to show icons for: `select all` and `delete`
* changes right view to show list and count of what is currently selected

Instead of clicking add to bench you can also drag to the bench icon in the top menu.

## mobile

Begin selection mode by pressing and holding any one item

* now tapping any item selects or deselects it
* switches top bar to info about how many selected + , `select all` icon, `delete icon` and `cancel` (actually we don't need cancel since the mobile back button should just intuitively cancel)

# top menu

Has a bench icon which when clicked on desktop gives a drop-down scrollable list of what's in the bench, where you can drag stuff out from that list into the inventory. This menu should support multi-select. It is fine if this drop-down completely covers the right side and uses nearly the exact same UI as the left side (minus the `+` button, breadcrumps, etc).

# moving items

## desktop

Moving can by done either by selecting one or more items and then clicking the +bench icon or dragging them to their new destination, where hovering over any navigable containers/breadcrumbs will navigate as if clicked. You will also be able to drag to the bench icon in the top right or drag to the +bench icon.

You will also be able to click the bench icon in the top menu to expand it down (as described above) and drag items from it, or drag the entire bench icon to drag move all of its contents.

## mobile

Moving is done by entering selection mode, then adding the selected items to the bench, navigation to the desired destination and emptying some or all items from the bench to that destination.

# left side

There is always a bench icon visible, no matter where you are in the inventory, to let you navigate to the bench.

## buttons

We'll only have one button on the left side:

* a round `+` button for "add to inventory" in the bottom right

This button will switch to "add to bench" when in selection mode, and when there is stuff in the bench it might turn into a two-button "pill" with one of the items being "put something from bench into the current container", but we might instead make that an additional option after clicking the + button.

The `favorite` and `edit` buttons will be moved in the top-right of the right side view so whenever a container is selected you will be able to toggle the favorite icon on and off for it, or click edit to switch the righ-side view

The `home button won't be there at all since there are other ways to navigate back (e.g. breadcrumbs).

# right side

The top area will always show name of container and the buttons/icons as described in the "buttons" section above.

* show photo, if there is a photo
* if no photo, show grid
* if no grid, show description of the container
* if not a container, show virtual info

The right side is position:fixed so it stays when you scroll down. It should always take up maximum verticall space. It should stop being position:fixed when you scroll all the way to the bottom so you can scroll down past it and see the bottom banner (with copyright info etc).

## container grid / container photo

* show multiple instances of the same virtual with the same color

# adding items

## desktop

Clicking the `+` add button will replace the UI on the left with a UI that gives you the options to:

* Add from bench (only visible if the bench is non-empty)
* Add container
* Add biomaterial

## Add from bench

### desktop

Opens the bench on the left side with the `+` add icon replaced by `add currently selected icons from bench` icon (maybe just a checkmark button). The right side view should be similar to selection mode, saying how many items are selected and listing them, but also telling you where the items will be moved. There should also be a big X or cancel button somewhere to cancel the "add from bench" operation.

### mobile

Again similar to the selection mode.

## Add container

### desktop

The left side should show first give you two options:

* Create new container
* Create biomaterial

The right side should initially show some text like: "Creating container in location <path>".

The `create container` mode should have a name text field, but when typing in it, an autocomplete-like list on the right side should be showing existing containers that match that name and some helpful text saying something like "You can select an existing container to base this container on it". When the cursor hovers over any items in the "auto-complete" list it a brief preview should show up with the image or n by m grid and the first couple of lines of the description.

If an existing container is clicked then all of the following fields will be pre-filled.

The next field should be a toggle: Grid or Photo (similar to the mobile toggle for toggling between left and right side views).

If toggled to Grid, beneath the toggle it should show two small text input fields for rows and columns, each with a horizontal slider next to it (make slider as wide as there is room). The grid will be shown in the right-side view. In fact, the right side view will just be a live preview of what the container will look like when clicked normally.

If toggled to photo then there will be a drag-drop area + browse buttonfor uploading a photo. When the photo is uploaded it will be shown in as full as full-screen as possible, this being the `edit hotspots` mode (see section on `edit hotspots`) Once the user clicks done they are returned to the form with the photo displayed as a thumbnail under the browse/upload controls with an "edit" link to open the hot-spot editor again.
  
You can leave either the image or grid blank and simply save and it will have neither an image nor a grid.

Then there should be a description textarea-like field which is also optional.

During the creation process there should be a round floating checkmark icon in the bottom right of the left area (where the `+` button normally is) which saves. It could alternately be a floppy save icon.

The 'create biomaterial' should be very similar to the container, except that if you don't select an existing virtual then it should have additional form fields for specifying the new virtual. When the "number of instances" field is focused, the right side should temporarily show a view of the photo or grid of the target container (assuming that container has a photo or grid) with a preview of where the new physicals will be placed and the ability to either click a new location to change where it will be placed (if there is only one instance) or click and drag the instances around (if there are multiple instances). There should be a toggle between "place all instances in same area" and "place all instances in different areas" (with a sane default, e.g. if adding more instances than the total number of areas then "place all instances in same area" should be the default). When the number of instances field is unfocused then the right side will return to a preview of what the physical will look like when clicked.

### mobile

We'll have to figure out a different way of doing the auto-complete but otherwise it should simply onle show the left side view and when clicking save it should go to a "place the physicals" view (the one that shows up on desktop when you focus the `instances` field).

# editing

Editing should use the exact same view as during creation.

# edit hotspots

This view is for editing the locations in a photo where physicals can be placed.

Two ways of specifying assignable areas:

* click and drag to create individual squares
* create an m by n grid on top of the image and resize

The first of these should be implemented first.

If nothing is specified then the photo should be thought of as one big area (same as a container with neither grid nor photo assigned).