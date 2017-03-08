<h1>Creating Your Model</h1>
After completing the [Introductory Tutorial](../getting_started/getting_started.md#introductory-tutorial), you can find additional information on using OpenStudio by topic below.

## Envelope
The building envelope is created using the SketchUp OpenStudio Plug-in. Refer to the [OpenStudio SketchUp Plug-in Interface Guide](../reference/sketchup_plugin_interface.md) to learn more about the interface and toolbars for the plug-in.

------

### Choosing a template
Templates contain data for constructions, loads, and schedules for 6 vintages across all U.S. climate zones. Templates do not contain any geometry. Load templates by using the menu under __Extentions/OpenStudio User Scripts/On-Demand Template Generators/Space Type and Construction Set Wizard__. Then select your type of building, vintage, and climate zone from the dialog. You can also get standard space types for that template by choosing "true" on the dialog. Space types can define internal loads, schedule sets, and construction sets.


![New OpenStudio Model From Template Dialog](img/menu_template.png)

*Above: Load a new template using the menu.*

![New OpenStudio Model From Template Dialog](img/from_template.png)

Vintages:

- DOE Ref Pre-1980
- DOE Ref 1980-2004
- DOE Ref 2004
- 90.1-2010
- 189.1-2009
- 90.1-2007

Climate Zones: 1 - 8

![Climate Zone Map](img/create_model/climate_zones.png)

------

### Creating and Customizing the Envelope
Drawing a floor plan in SketchUp and extruding up from floor plan using the "The Space Diagram" tool(![New Space Diagram Icon](img/plugin_reference_guide/extrude.png)) is one way to create your envelope. The video below demonstrates this workflow.

Creating geometry from photographs is another option. To learn more about it watch the [photo matching tutorial playlist on YouTube](http://youtu.be/6IPZIrpl5vs?list=PL8CC6E4D9908F17BF).

<iframe width="640" height="360" src="http://www.youtube.com/embed/wzzY_W2WELo?start=44&end=129" allowfullscreen></iframe>

*Above: This video shows you how to create your building envelope. It uses the OpenStudio SketchUp Plug-in.*

After defining the building envelope, you use the Surface Matching tool to set the boundary conditions. These will allow thermal connections between spaces and will inform OpenStudio about what construction to apply.

------

### Fenestration
There are many ways to add windows to the building envelope.

- Use the "Project Loose Geometry" tool for adding window.

<iframe width="640" height="360" src="http://www.youtube.com/embed/wzzY_W2WELo?start=129&end=171" allowfullscreen></iframe>

*Above: This video shows how to create windows using the "Project Loose Geometry" tool.*

- Set a window to wall ratio, for the whole building or for space type, by selecting all or just a space and going to `Plugins->OpenStudio User Scripts->Add or Alter Model Elements->Set Window to Wall Ratio` and edit or use defaults. This script will remove all existing windows.

![User Script Menu](img/create_model/plugin_window_to_wall_1.png)

*Above: Menu for setting the window to wall ratio using an OpenStudio script.*

![Window-to-Wall Ratio Dialog](img/create_model/plugin_window_to_wall_2.png)

*Above: Dialog for setting the window to wall ratio.*

------

### Defining Conditions for Heat Transfer Through Surfaces
- Choose the "Render by Boundary Condition" (![Render by Boundary Condition Icon](img/plugin_reference_guide/render_boundary.png)) setting.
- Check your model to make sure the boundary settings are correct. *Blue* indicates exterior surfaces, *green* indicates interior walls, and *brown* indicates floors. You can use the SketchUp "Section Plane" tool to view a cross section of the model and see interior surfaces.
- If you have *green* surfaces on the outside of the model, use the Surface Matching (![Surface Matching Tool Icon](img/plugin_reference_guide/SurfaceMatchingSelected-24.png)) tool to open up the dialog and hit "Intersect the
Entire Model." This will not work if you are inside a single space when you run it.
- Then select "Match the Entire Model" to correct the model.

![Surface Matching](img/create_model/surface_matching.png)

*Above: Surface Matching window shown.*

<!--
### Air Walls

------

### Interior Partition Groups
-->

------

### Site Shading
To create a shading group use the "New Shading Group" (![New Shading Surface Group](img/plugin_reference_guide/NewShading-24.png "New Shading Shading")). The new group looks like a transparent purple box. Double click on box to enter the group and draw the shading surface.

![Surface Shading Group](img/create_model/shading_group.png "Surface Shading Group")

*Above: Surface Matching dialog shown.*

Add overhangs by:

- Drawing the shading surface using the SketchUp drawing tools or use a script to add.

![Shading](img/create_model/draw_shading.png "Draw Shading Surface")

*Above: Shading can be drawn on using photo matching.*

- Using a script to automatically add overhangs.

<iframe width="640" height="360" src="http://www.youtube.com/embed/wzzY_W2WELo?start=295&end=360" allowfullscreen></iframe>

*Above: This video shows you how search for specific surfaces and use a script to add overhangs to those surfaces.*

<!-- ### Building Rotation -->

## OpenStudio Application
To assign schedules, add loads, add HVAC systems, and more, open your model in the OpenStudio application. Open your model directly from the SketchUp Plug-in by hitting the OpenStudio icon on the toolbar or by opening a file from the OpenStudio application.

![Open Model In OpenStudio Application](img/create_model/open_app.png)

*Above: Select the OpenStudio icon to open the file and edit it in the OpenStudio application.*

------

## Site
Under site you can add the weather file, import design days, and set the year. 

You can set the day of the week the simulation should start or select a calendar year. Use a calendar year if you are going to calibrate the model with utility bills.

The tab can also be used to configure and turn daylight savings time on and off.

[![Site Weather and Design Days](img/create_model/weather_ddy_new.png "Click to view")](img/create_model/weather_ddy_new.png)

*Above: Add weather file, select year, and import design days.*

------

## Schedules
To create and edit schedules in the OpenStudio application go to the schedules tab. Check out the [OpenStudio Application Interface Guide](../reference/openstudio_application_interface.md) for an overview of the interface.

------

### Inspecting and Adjusting Schedule Sets
A Schedule Set is a collection of schedules for building activities or elements.

A schedule set can be applied to an entire building, a story, a space type, or an individual space.

This sub-tab has two kinds of drop zones. You can drop schedule sets from My Model or Library into the bottom of the left pane, or you can drop individual schedules into the drop zones in the main body.

![Schedule Sets Tab](img/create_model/schedule_sets.png)

*Above: Create and edit schedule sets.*

------

### Inspecting and Editing Ruleset Schedules
This tab is a visual editor for Ruleset Schedules. As the name implies, a schedule consists of a series of rules. Each rule or profile can be applied for a specific date range and for specific days of the week.

If two rules appear on the same day, the one with a higher priority is used. You can use the rule colors to visually scan the entire year in the calendar on the right of the body to see what rule is applied for a specific day.

A new profile starts as a flat line. Double click to split the profile and then drag one segment up or down. Vertical sections can also be dragged left or right. Click Set Limits to change the vertical limits of your profile. To type precise values for a profile, mouse over the profile and enter a value with your keyboard.

Although you can use Compact and other schedule types in your model, you can visualize and edit only Ruleset Schedules in the OpenStudio application.

The lower profile view is a navigation for when you are zoomed to 15-minute or 1-minute time steps.

[![Schedules Editor Tab](img/create_model/schedules.png "Click to view")](img/create_model/schedules.png)

*Above: An annotated screenshot of the schedules editing interface. Click image for a large view of the image.*

<iframe width="640" height="360" src="http://www.youtube.com/embed/PCcxruCaZO0?start=210&end=788" allowfullscreen></iframe>

*Above: This video demonstrates how you can inspect, alter, and apply resource objects in an older version of the  OpenStudio Application.*

<!--
- Assigning Schedules and Schedule Sets
- Other Types of Schedules
    - Constant
    - Compact
-->

------

## Constructions
In an energy model, each surface must have a construction assigned. The construction determines the heat transfer through that surface. A construction set can be applied to an entire building, a story, a space type, or an individual space. Usually a majority of the exterior walls in a building will share the same construction. You can assign the exterior wall construction on the building level and that construction will be applied to all exterior walls. This will be the default construction, but you can still edit surfaces and subsurfaces that differ from the defaults.

### Construction Sets
A Construction Set object is structured very much like the Schedule Set. It can contain constructions for different surface types and boundary conditions.

Construction sets do not have to be complete sets. For example, you can have a construction set assigned to a story that has only an exterior wall. For the rest of the surface types, constructions will be inherited from the building object.

![Construction Sets Tab](img/create_model/construct_sets.png)

*Above: This screenshot shows an example of a construction set added from the library.*

<iframe width="640" height="360" src="http://www.youtube.com/embed/8KdVvBds_30" allowfullscreen></iframe>

*Above: This video shows you how to obtain construction and material objects from the Building Component Library and load them into your current model.*

------

### Constructions
The Constructions sub-tab lists construction objects that are in your model. You can drag additional constructions here from the library. Constructions download using the Online BCL window will appear in the library with a "BCL" flag.

A construction consists of one or more material layers. You can add materials by dragging them from My Model or the Library to the drop zone. You can only add new materials to the bottom which represents the inside of the wall. You can delete any material by clicking the `x` next to the name.

![Constructions Tab](img/create_model/constructions.png)

*Above: Edit and create constructions on this tab.*

------

### Materials
Constructions are made of one or more layers of materials. The Materials sub-tab lets you inspect and edit those materials.

There are various classes of material objects. When you add a new material, first select the heading for the type of material you want to add and then click the "+" icon at the bottom of the left pane.

Different types of material will have different data fields available.

Materials also have "Measure Tags" as optional inputs. These tags can be used by measures or they can be used for [exporting a file for a Title 24 Compliance tool.](tutorial_cbecc_materials.md) 

![Materials Tab](img/create_model/materials.png)

*Above: Edit and create materials on this tab.*

<!--
Tutorials

- Inspecting and Adjusting Construction Sets
- Adding and Removing Materials from a Construction
 
Resources

- Types of Constructions
- Types of Materials
- Proper Use of Constructions
-->

------

## Internal Loads
The Loads tab allows you to create and edit load definitions for the internal load objects you will use in your model. Types of loads are listed in the right panels. Select the type of load you want to create and hit the plus button or drag a load definition from the library onto the drop zone in the lower right.

Once you add a loads definition, it will be available to use from the "My Model" tab on the right panel. On the Space Type tab you can assign loads to a space type or directly to a space in the Facility tab, except for Water Use Equipment.

![Load Definitions](img/create_model/load_def.png)

The types of loads that can be added in this tab follow:

- People
- Lights
- Luminaires
- Electric Equipment
- Gas Equipment
- Steam Equipment
- Other Equipment
- Internal Mass
- Water Use Equipment

Internal mass is different from the other loads in that it does not use fuel; rather, it stores heat and then dissipates the heat over time. The inputs require a surface area
assigned to a construction object.

Water Use Equipment is also unique in that it takes schedules, and is not part of a space type. Water Use Equipment is applied in the HVAC Systems Tab.

<iframe width="640" height="360" src="http://www.youtube.com/embed/PCcxruCaZO0?start=106&end=209" allowfullscreen></iframe>

*Above: This video demonstrates how you can inspect, alter, and apply resource objects in the OpenStudio Application.*

<!--
#### Tutorials
- Adjusting Internal Loads
- Increasing Fidelity of Internal Loads

#### Resources
- People
- Lights
- Luminaires
- Electric Equipment
- Gas Equipment
- Steam Equipment
- Other Equipment
- Internal Mass
- Water Use Equipment
-->

------

## Space Types
Space types can define internal loads, schedule sets, and construction sets.cSpace types define specific spaces or groups of specific spaces in your model. The spaces inherit all objects of the space type. If you redefine a space type, or an underlying object, it will affect all spaces using that space type.

The space types tab in the OpenStudio application is organized into a grid view. You can look through all your space types and edit the settings.

<!--
- Inspecting and Adjusting Space Types
- Assigning Space Types and Default Space Types
-->
[![Space Types General](img/create_model/space_types_general.png "Click to view")](img/create_model/space_types_general.png)

*Above: The grid view provides a spreadsheet style layout.*

### Editing Multiple Items
You are now able to check rows and then select an item you want to apply to those rows. When you hit the "Apply to Selected" the yellow selected item will be copied to the checked rows.
 
[![Space Types Multiedit](img/create_model/space_types_multiedit.png "Click to view")](img/create_model/space_types_multiedit.png)

*Above: You can apply settings from one space to other using the "Apply to Selected" button at the top of the columns.*

### General
#### Rendering Color
This feature can be adjusted in the SketchUp Plug-in as well and the color selected will be used in the other application as well.

![Rendering Color Dialog](img/create_model/space_types_render.png)

#### Default Construction and Schedule
You can assign constructions and schedules to each space type that will be used whenever that space type is used in the model.

#### Design Specification Outdoor Air
This drop zone is located under the "General" button.

#### Space Infiltration Design Flow Rates and Space Infiltration Effective Leakage Areas
These can be added and edited under the "General" button by scrolling to the right. Drag-and-drop from library.

### Loads
If you select the "Loads" button in the Space Type tab, you will see a drop zone to create new loads. You can have multiple loads of the same type.

[![Schedules Editor Tab](img/create_model/space_types_loads.png "Click to view")](img/create_model/space_types_loads.png)

*Above: Hit the "Loads" button to edit and view loads by space type. Click on the name of a component and select the "Edit" panel on the right to inspect, edit, or delete that item. You can edit the load definition in the example shown above.*

The space types define loads such as lighting or electric equipment as simple area weighted power densities (e.g., W/ft2). However, you can add loads in several possible ways. For example, a space type could contain multiple types of lighting. You might define one lighting load for general lighting using a W/ft2 and then add another lighting load for decorative lighting using another watts per square foot.

### Measure Tags
Measure tags are used by scripts we call measures. Measure tags identify intended use of space types and constructions for School and office AEDG measures. If you are not using measures you will not need to complete these.

<iframe width="640" height="360" src="http://www.youtube.com/embed/uxpIcEbxPbw" allowfullscreen></iframe>

*Above: This video shows how to use measure tags.*

### Custom
Use the checkbox at the top of each column to select items that you want to have be part of the custom view in the grid. This allows you to compare important settings side-by-side.

### Working with Space Types in the SketchUp Plug-in
The video below shows how to work with space types in the Plug-in.

<iframe width="640" height="360" src="http://www.youtube.com/embed/8LTexVna_vw?end=234" allowfullscreen></iframe>

*Above: This video shows you how to assign space types and download space types from the Building Component Library (BCL). It uses the OpenStudio SketchUp Plug-in.*

------

## Downloading Components and Measures from the Building Component Library (BCL)
In the OpenStudio Application you can download items directly from the BCL by going to the "Components & Measures" menu and choosing "Find Measures" or "Find Components." Your API key is available by registering on the [BCL site](https://bcl.nrel.gov/) and copying it from your account page.

![BCL Dialog](img/create_model/bcl_window.png)

The components are designed to provide data to the energy modeler and simplify the process of gathering inputs.

Measures are scripts that can quickly alter your model or create different reports for viewing and checking your results. Learn more about measures in the [About Measures](../getting_started/about_measures.md) section. Learn how to [write your own custom measures](../reference/measure_writing_guide.md).

------

## Using the Facility Tab 
The Facility tab includes settings for your building, stories, shading, and exterior equipment. It used to be a tree view, but this did not allow the user to view more than one item at a time. You can view the Building object. This contains top level construction, schedule, or space type assignments, and sets the rotation for the building.

To view and edit the spaces in your model, use the Spaces tab below the Facility tab on the left.

<iframe width="640" height="360" src="http://www.youtube.com/embed/9uBcb3NBQ84" allowfullscreen></iframe>

*Above: This video demonstrates the new Spaces tab and the redesigned Facilities and Site tab.*

![Facility Tab](img/create_model/facility.png)

*Above: A screenshot of the facilities tab with the building sub-tab selected.*

![Annotated Facility Tab](img/create_model/facility_strories.png)

*Above: this screenshot shows the contents of the stories tab. You can add and edit story settings here.*

------

## Spaces
The new spaces view lets you edit the spaces and view the surfaces and sub-surfaces in those spaces. The Story, Thermal Zone, and Space Type filters can help you find a particular space to edit.

Some items are not editable in the OpenStudio application and have to be edited in the SketchUp Plug-in. Use the horizontal tabs to inspect and edit space attributes. 

* Properties
* Loads
* Surfaces
* Subsurfaces
* Interior Partitions
* Shading

Each horizontal tab may have sub-buttons that hold additional settings.

[![Spaces Properties](img/create_model/spaces_properties.png "Click to view")](img/create_model/spaces_properties.png)

*Above: The sub-buttons under the Properties tab are General, Airflow, and Custom.*

[![Spaces Surfaces](img/create_model/spaces_surfaces.png "Click to view")](img/create_model/spaces_surfaces.png)

*Above: The spaces in your model are listed with all their surfaces under the Surfaces tab.*

[![Spaces Subsurfaces](img/create_model/spaces_subsurfaces.png "Click to view")](img/create_model/spaces_subsurfaces.png)

*Above: The subsurfaces are organized under the space they belong to and the surface they are connected to is displayed as well.*

------

## Thermal Zones
OpenStudio's thermal zones parallels the EnergyPlus zone. A thermal zone represents an isothermal volume of air that may have only one thermostat. The OpenStudio thermal zone forms the connection point between the air conditioned space and the  HVAC equipment. Thermal zones can contain one or more spaces. An OpenStudio space contains 3 dimensional geometry and thermal loads. When OpenStudio performs an EnergyPlus simulation, the space objects associated with each thermal zone are geometrically combined, the space loads are averaged, and the ventilation rates from each space are added together.

Setting up thermal zones in the SketchUp Plug-in is shown below.

<iframe width="640" height="360" src="http://www.youtube.com/embed/8LTexVna_vw?start=240&end=438" allowfullscreen></iframe>

*Above: This video shows you how to assign space types and download space types from the Building Component Library (BCL). It uses the OpenStudio SketchUp Plug-in.*

A thermostat must be defined before running an EnergyPlus simulations with connected HVAC systems. Zone equipment, thermostat, and humidistat settings can be viewed and edited on this tab. Click on the name of and item and you can inspect it in the "Edit" panel on the right.

![Thermal View](img/create_model/thermal_grid.png)

*Above: Screenshot of the OpenStudio application thermal view with "HVAC" selected.*

Select the "Cooling Sizing Parameters" or "Heating Sizing Parameters" to edit those by thermal zone.

![Thermal Zone Sizing Parameters](img/create_model/heat_sizing.png)

*Above: Screenshot of the OpenStudio application thermal view with "Heating Sizing Parameters" selected.*

------

## Air, Plant and Zone HVAC Systems
The HVAC Systems tab is used to create, inspect, and edit air and plant loops. The green `+` at the top left is used to add template or empty loops, and the `x` next to it will delete them. The pull-down at the top right of the body is to select which loop to displayed.

Hit the green plus button to add a loop.

![Add HVAC System Dialog](img/create_model/add_hvac.png)

*Above: Add an HVAC system to your model.*

When adding a template loop, there are four images within the icon. From left to right they represent the type of cooling, heating, fan, and terminal unit, in the template. The example below has cold and hot water, a variable speed fan, and a hot water reheat terminal unit.

![System Template Icons](img/create_model/system_templates.png)

The top half of the loop is for supply-side objects, the bottom half is for demand. Thermal Zones and other objects can be dragged onto drop zones or nodes. Optionally you can select the splitter or mixer to bring up a list of Thermal Zones, checking the ones you want included in the loop.

OpenStudio names HVAC systems and components to match EnergyPlus. So if you are familiar with EnergyPlus you will be able to recognize components names, like FanConstantVolumeModel.

![HVAC Interface](img/create_model/hvac_about.png)

*Above: Annotated view of the HVAC interface.*

![Add Thermal Zone](img/create_model/add_thermal_zones.png)

*Above: Another way to add thermal zones, besides dragging them from the "My Model, is to select the splitter or mixer and check the boxes on the right panel.*

![Edit Component](img/create_model/component_edit.png)

*Above: Select a component and edit it on the "Edit" tab on the right panel. Some components like the one above will have icons under the "Edit" panel. The gear icons will let you edit the component's settings.*

![Adjust Connections](img/create_model/connections.png)

*Above: Select a component and adjust the connections, by hitting the link icon on the "Edit" tab on the right panel.*

![Adjust Controller on Component](img/create_model/hvac_controller.png)

*Above: Select a component and adjust the controller, by hitting the dial icon on the "Edit" tab on the right panel.*

The __control view__ is only available for the air loops. With an air loop selected in "Layout" view you can switched to "Control" view. In this view you can edit the time of operation, night cycle, supply air temperature, and mechanical ventilation.

![Air Loop Control View](img/create_model/hvac_control.png)

*Above: Control view only available for air loops.*

------

### Cold Water Loop
In the cold water loop the cooling coil that had been a supply side object on the air loop is now a demand object.

The supply side has a pump and a water cooled chiller. The adiabatic pipes are a necessary part of the loop. There are no attributes to set for the pipes.

You can click on the chiller to drill down further to the condenser loop. Or you can click on the cooling coil to go back to the air loop.

[![Chilled Water Loop](img/create_model/chilled_water.png "Click to view")](img/create_model/chilled_water.png)

*Above: Click image to view a larger version.*

------

### Condenser Loop
In the condenser loop the chiller that had been a supply side object on the cold water loop is now a demand object.

The supply side has a pump and a cooling tower. As with the cold water loop the adiabatic pipes are a necessary part of the loop.

You can click on the chiller to drill to go back to the cold water loop.

[![Condenser Water Loop](img/create_model/condenser_water.png "Click to view")](img/create_model/condenser_water.png)

*Above: Click image to view a larger version.*

### Hot Water Loop
In the hot water loop the heating coil that had been a supply side object on the air loop is now a demand object.

The supply side has a pump and a boiler. The boiler can use a variety of fuels. The adiabatic pipes are a necessary part of the loop. There are no attributes to set for the pipes.

You can click on the heating coil to go back to the air loop.

The heating coils without links represent the reheat terminals for each connected thermal zone.

[![Hot Water Loop](img/create_model/hot_water.png "Click to view")](img/create_model/hot_water.png)

*Above: Click image to view a larger version.*

------

## Return and Supply Plenums
To add supply and return plenum zones:

1. Access the plenum editor by selecting the zone on the layout view.
2. Select the "Edit" tab on the right panel and click on the  plenum icon on the blue bar.
3. Choose a plenum from the drop down list or create a new plenum zone but selecting the green add button. The zones available to be plenums will be selectable in a dialog. Create new zones for plenums in the Thermal Zones tab on the left.

Shared plenums will be colored the same and will match the color selected for the plenum zone on the Thermal Zones tab.

[![Plenum Diagram](img/create_model/plenum_noted.png "Click to view")](img/create_model/plenum_noted.png)

*Above: Click image to view a larger version.*

<iframe width="640" height="360" src="http://www.youtube.com/embed/n_u3WT2tX1Y" allowfullscreen></iframe>

*Above: This video demonstrates how to create the geometry for and then hook up supply and return air plenums.*

------

<!--
## Radiant Systems

------
-->

## Service Water Heating
The first view into the HVAC tab will be the water mains editor, which shows as "Service Water" on loops dropdown list.

Water enters the system at the right and leave at the Sewer on the left. One or more water use connections can be added in the middle.

[![Service Hot Water](img/create_model/water1_large.png "Click to view")](img/create_model/water1_large.png)

*Above: Service hot water interface. Click the image to view larger version.*

Clicking a water use connection will take you to a model window where you can add water use equipment.

[![Water Use Connection](img/create_model/water2_large.png "Click to view")](img/create_model/water2_large.png)

*Above: Service hot water interface. Click the image to view larger version.*

Dragging a water use equipment object into the water use connection will create an instance of that definition. Much like lights, people and other loads, there is a fractional schedule to define usage patterns.

Optionally you can associate the equipment with a space. There is no direct energy use to the space, but heat from the equipment will be added to the space.

The equipment can be anything that uses water, hot or cold. The definition contains a peak flow rate and a target temperature schedule. Hot and cold water will mix to reach the target temperature at the fixture.

Click the water main, sewer, or makeup water to go back to the water mains editor. If you have a plant loop associated with the water use connection the "Loop" button will take you to the loop.

<iframe width="640" height="360" src="http://www.youtube.com/embed/jUJhi6YH51E?end=486" allowfullscreen></iframe>

*Above: This video shows you how create models using service hot water. This includes water heaters, water use connections, water use equipment, and other associated objects.*

------

## Refrigeration
The refrigeration system interface can be accessed by selecting refrigeration from the drop down menu.

To add a refrigeration system select one from the library and add drag it to the drop zone.

Click on the zoom button by the name of the refrigeration system to go to a view of that system, add components from the library.

[![Refrigeration System](img/create_model/refrig_grid.png "Click to view")](img/create_model/refrig_grid.png)

*Above: Add refrigeration systems to your model under the HVAC tab. Click image to view a larger version.*

This zoomed in view provides the layout view of one refrigeration rack. You may add cases by dragging them on to the "Drag and Drop Cases" drop zone.

Drop zones are provided to accommodate systems with a mechanical sub-cooler and a Suction Line Heat Exchanger (SLHX).

The small arrow at the bottom of the refrigeration case summary will open and expanded view of cases. Each case can be selected and edited in the Edit panel on the right.

Cascade systems can be added by dragging the from "My Model" or the "Library."

[![Refrigeration System](img/create_model/refrig_2_large.png "Click to view")](img/create_model/refrig_2_large.png)

*Above: Single refrigeration system view. Click image to view a larger version.*

An alternate view of the refrigeration systems is provided by the grid view. The refrigeration grid view provides a method for entering case settings in a spreadsheet style. Cases can be added, assigned to racks, and edited in this view.

There are two major divisions, one for Display Cases and another for Walk-ins. Under each division a drop box is available to add new cases. There are also buttons to move through the case settings and enter the data on each case.

Create your own custom view of this information by checking the box on the right of the column header. Checked columns will show up under the Custom button.

[![Refrigeration Grid View](img/create_model/refrig_grid_large.png "Click to view")](img/create_model/refrig_grid_large.png)

*Above: Click image to view a larger version.*

<iframe width="640" height="360" src="http://www.youtube.com/embed/iHTDiHif2_U" allowfullscreen></iframe>

*Above: This video demonstrates the new refrigeration features added to OpenStudio 1.2.0. These feature will be expanded in future releases.*

<iframe width="640" height="360" src="http://www.youtube.com/embed/NRo9k0Rjfw8?start=57&end=166" allowfullscreen></iframe>

*Above: The video above provides an introduction to the grid view provide for refrigeration.*

In the initial release of the grid view, no provision was made to delete a case or walk in; they must be must be assigned to a rack, and deleted from the layout view. This functionality omission will be corrected in the next OpenStudio release.

------

## VRF Systems
Variable refrigerant flow (VRF) systems can be added by dragging them onto the large drop zone from the library.

The layout view provides a view of all the VRF systems in the model. The zoom icon by the name of the system will open a detailed view of that system.

[![VRF Layout](img/create_model/vrf_layout_large.png "Click to view")](img/create_model/vrf_layout_large.png)

*Above: VRF system layout view. Click image to view a larger version.*

To create your VRF system, start by dropping a terminal from the "Library" onto the drop zone. Then add thermal zones from "My Model." When a thermal zone is added a new VRF terminal will automatically be created.

[![VRF Single Layout](img/create_model/vrf_zoom_large.png "Click to view")](img/create_model/vrf_zoom_large.png)

*Above: VRF system single system layout view. Click image to view a larger version.*

Set the terminal settings by selecting the terminal and editing in the "Edit" tab on the right.

More than one terminal can connect with the same zone. Just drag the zone to the drop area again to add another connection.

<iframe width="640" height="360" src="http://www.youtube.com/embed/NRo9k0Rjfw8?start=170&end=242" allowfullscreen></iframe>

*Above: This video provides a brief overview of the VRF interface.*

------

## Apply Measure Now
Now in addition to manually creating and editing your model, you can apply measures to your model live in the application. This allows you to customize your experience to your desired workflow. Measures can manipulate any part of the model and can also be used as a diagnostic tool.

![Apply Measure Now Menu](img/create_model/apply_now.png)

*Above: Select the "Apply Measure Now" from the menu.*

![Apply Measure Now Dialog](img/create_model/apply_now_1.png)

*Above: Select measure.*

![Apply Measure Now Dialog Accept](img/create_model/apply_now_2.png)

*Above: Accept or cancel.*

The video below demonstrates the use of this feature.

<iframe width="640" height="360" src="http://www.youtube.com/embed/9-saA4x07eQ?end=579" allowfullscreen></iframe>

*Above: Use the Apply Measure Now function.*

------

##  Using the Measures Tab
The measures selected on this tab will not run until you run your model, unlike the "Apply Measure Now" option.

Download additional measures from [The Building Component Library (BCL)](http://bcl.nrel.gov/). Drag measures from the library to the central panel.

There are three types of measures:

1. __OpenStudio Measures__ are run on the OSM model before it is converted to an IDF.
2. __EnergyPlus Measures__ can be run on the IDF file before it is handed to EnergyPlus.
3. __Reporting Measures__ produce reports to chart results, provide quality assurance, and quality control on models.

![Measures Tab](img/create_model/measures.png)

*Above: Select measures from the library and drag them into the correct drop zone.*

By selecting the measure and selecting the right "Edit" tab, inputs for the measure can be entered and adjusted.

![Measures Tab Fields](img/create_model/measures1.png)

*Above: Select a measure and edit the fields in the right panel.*

------

## Lifecycle Costs
The most basic parameters needed for a life cycle cost analysis are the analysis period length and the discount rate. A longer analysis period accumulates more energy cost savings than a shorter period; giving energy conservation measures a better pay back relative to their initial costs. A higher discount rate devalues future energy cost savings relative to money spent on capital improvements in the present; giving energy conservation measures a lower pay back relative to their initial costs. This tab allows users to set these parameters on their baseline model.

With measures, downloaded from BCL,  life cycle costs for different design alternatives can be calculated

![Measures Tab Costs](img/create_model/lifecycle_costs.png)

*Above: Add costs to measures to calculate and compare different options. This can also be done in the Parametric Analysis Tool.*

------

## Calibration with Utility Bills
Add utility bills for calibration on the Utility Bills Tab under Site.

First, you must __select a weather file__ and __a year__ before you can enter the bills.

1. Select the type of utility on the left.
2. Hit the plus button to add bills.
3. Name the Bill and complete the units fields.
4. Select the billing period inputs and hit the plus sign to add a bill.

To calibrate to the ASHRAE 14-2002 or FEMP standard the file must contain all utility data for one year and real weather data. Check the guidelines for additional requirements.

![Utility Bills Tab](img/create_model/utility_bills.png)

*Above: A screenshot of the Site Utility Bills sub-tab.*