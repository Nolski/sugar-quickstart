Sugar_Activity_QuickStart
=========================

This is the framework for a Sugar Activity.  Everything needed to quickly start an activity for the Sugar OLPC XO.\
Credit fot this repo is given to Robin Brooke. His blog: http://rbrooke.blogspot.com/2010/01/creating-xo-file.html
**NOTE: you do not NEED to create a MANIFEST file. It is not integral to the sugar XO.

Included in this QuickStart:

	-activity directory (folder)
		-activity.info
	-setup.py
	-README.md (this file)
	-activity.py (this is empty)
	
What is not included in this Quickstart(you make these):
	-icon.svg
	-an actvity.py file
	-a dist folder with a .xo file



Files needed:
1.)Activity.py

-Needs to be coded in python
-Needs to be placed into a class structure

2.)Icon 

	-Needs to be an .svg (scalable vector graphic) file format
	-Inkscape is a wonderful program to make svg's and choose it's icon_48x48 pxls
	
	-included code:
	
		PART ONE:
		
			Before:
			<?xml version="1.0" encoding="UTF-8" standalone="no"?>
			<!-- Created with Inkscape (http://www.inkscape.org/) -->
		
			After:
			<?xml version="1.0" ?><!DOCTYPE svg PUBLIC '-//W3C//DTD SVG 1.1//EN' 'http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd' 
			[<!ENTITY stroke_color "#000000">
			<!ENTITY fill_color "#FFFFFF">]><svg

		Part TWO:
		
			Before:
			<rect
			style="fill:#ffffff;stroke:#000000;stroke-opacity:1"
			id="rect904"
			width="36.142857"
			height="32.142857"
			x="4.1428571"
			y="7.1428571" />
			
			After:
			<rect
			style="fill:&fill_color;;stroke:&stroke_color;;stroke-opacity:1"
			id="rect904"
			width="36.142857"
			height="32.142857"
			x="4.1428571"
			y="7.1428571" />
			

	Explanation:
		-Once your icon is finished, load it into any text editor and edit the above lines
		-In the body of the file, change the references to FILL and STROKE within 
		 the attribute STYLE
		 -
		


3.)activity.info 

	-Contains all the file linkage that the OLPC XO needs to run your activity

	-included code:

		[Activity]
		name = (name of your activity)
		bundle_id = example
		icon = exampleicon
		exec = sugar-activity exActivity.exampleActivity
		show_launcher = yes
		activity_version = 1
		license = GPLv2+

	Explanation:
	name : The name of the activity as the user sees it

	bundle_id : A unique name that Sugar uses to refer to your activity. 
				The journal also stores this name in the metadata of your 
				activity entry, so you can resume this activity from the entry.

	icon : The name of your icon. It must be an svg file.  example: "myicon.svg"

	exec : Tells Sugar how to launch your Activity. It tells sugar to create an instance
		   of the class exampleActivity which it finds in the exampleActivity.py
	
	show_launcher :  The first is to click on the icon
					 in the Activity view. The second is to resume an entry in the journal.
	
	activity_version : An integer that displays what iteration your activity is.
	
	license : A license tells people what they can and can't do with a program.  
			  GPLv2+ is a popular standard license.

4.)setup.py file

	-This file runs to build the .xo file that the OLPC needs to run.

	-included code:

		from sugar.activity import bundlebuilder
		bundlebuilder.start()


5.) activity directory

	-This folder will hold your activity.info file and your icon.svg
	


How to build a sugar XO:
1.) Method 1:

	a.)	In home/Activities/example, type:

			./setup.py dev
		
	b.)	In home/Activities/example, type:
	
			/setup.py dist_xo
		
		
	Explanation:
	a.)-The activity needs to be installed. This method creates a symbolic link within the OLPC.  A symbolic link is a 
	way of make a directory or file appear to be located in two places without having to copy it.
	b.)-This will create the xo file and place it in a new folder called dist in the Activity directory
	
	
2.) Method 2 (in linux):

	a.) Open a terminal and navigate to your activity folder, type:
		
		python setup.py dev
		
	b.) Then type:
		
		python setup.py dist_xo
		
	c.) Pull .xo file out of the dist folder you just created and place it onto a flash drive.
	
	d.) Copy the .xo file from the flash drive into the Journal of the OLPC
			
	

	Explanation:
	a.)- Same explanation as above.
	b.)- Creates a 'dist' folder containing the .xo file within your activity folder.
	c.)- Instructions on how to get the .xo file onto the sugar OLPC
	d.)- The activity should now show up in the journal and on the home circle.
	**NOTE: If your activity icon doesn't load correctly, there is something wrong with your activity.info file.
			Please check to make sure each of your values are complete and correct.
			