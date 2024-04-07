# VSD SOC Design using OpenLANE

### Day-wise Checklist
- [x] [**DAY - 1**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-1) <br>
- [x] [**DAY - 2**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-2) <br>
- [x] [**DAY - 3**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-3) <br>
- [ ] [**DAY - 4**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-4) <br>
- [ ] [**DAY - 5**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-5) <br>
<br>
Author: Indrani Aekabote

#### Created a VM on my laptop.
![Screenshot 2024-03-27 222647](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/d30d2ee7-ad5a-4657-b7a1-c656fcd73c72)

## [DAY-1 (Calculating the flop ratio)](https://github.com/sagainfinite/vsdcourse_indrani?tab=readme-ov-file#DAY-1)

### Chip area 
![chip area](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/da1d0c4d-3c2d-4979-85d4-03ecf65a6356)

### Flop Ratio = $`\frac{Number of D-FFs}{Total number of cells} `$
#### Number of D-FFs
![no  of d_ffs](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/53449890-43c2-4eeb-b1a1-d73a3ad5c075)

#### Number of Cells
![no  of cells](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/ae1ecdfc-1501-4b8e-80f7-c5552ad51cbe)

### Flop Ratio = $`\frac{1613}{14876}`$
                = 0.1084
                = 10.84%
### List of reports generated after the synthesis was run
![report list](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/55bd297e-e383-4568-8388-4749149fc295)
### STA report details 
![sta_report](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/3bf784df-ce7f-4518-9421-3f6fdde7647a)

## [ DAY-2 (Determine Die Area alongwith floorplan and placement in Magic)](https://github.com/sagainfinite/vsdcourse_indrani?tab=readme-ov-file#DAY-2) <br>
#### PART 1: Die Area 
#### PART 2: Floorplan
#### PART 3: Placement

### PART 1: Die Area <br>
#### Area of die (in microns) = width X height 

##### Figure: Die coordinates in picorv32a.floorplan.def 
![die area](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/c8d68221-1740-48d1-bb24-3f04fd207791)
 #### 1 micron (µm) = 1000 units
 #### (X,Y) initial coordinates = (0,0)
 #### (X,Y) final coordinates = (660685,671405)
 #### Width (in µm) = $`\frac{660685}{1000}`$ = 660.685 µm
 #### Height (in µm) = $`\frac{671405}{1000}`$ = 660.685 µm
 #### Area of Die (in µm) = 660.685 X 660.685 = 443587.2124 µm² (square microns)
 
<br><br>
##### The logic to be implemented 
![logic tbi](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/03eb6ed4-493d-4631-901d-4c98575b7c32)
<br><br>
### PART 2: Floorplan
<br>

##### Figure: pre-set values/default values
![pre-set values](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/4dd6e8c0-afa5-41c1-82a5-57ea846b88c2)
<br>
##### Figure: SCL config
![SCL config](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/4356dd69-7979-4c8d-91a7-a7fd401eed7a)
<br>

##### Figure: floorplan values
![floorplan values](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/fe430187-56b0-436a-8e70-0f99966a8484)
<br><br>
##### Figure: Floorplan with values for:
##### > core utilisation
##### > aspect ratio 
##### > vmetal and hmetal
![floorpllan_tcl descp](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/41e1e13e-9268-4253-9196-ce74d3259a02)
<br><br>
##### Figure : Values to work with 
![values to work with](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/baf32b2d-26e1-4476-84a6-d963182273b6)  
<br><br>
##### Figure: clock details in config.tcl file 
![config_tcl description](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/fa92c418-65ea-4153-9285-ff15aade57d9)
<br><br>
#### Run Floorplan and Open layout in Magic 
            % run_floorplan
            
            # Command to run floorplan in Magic
            >> magic -T/home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
##### picorv32a.floorplan.def in Magic
![layout in magic](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/66f723cc-3f6d-4b4c-9415-d338282b77e9)
<br><br>
##### I/O ports are equidistantly placed
![equi-dist pins](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/61d27fb9-2b4e-46ba-8743-5b80fd2ef0c0)

##### Tap cells are equidistantly placed
![equi-dist taps](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/a87260cd-d95b-4a88-834d-b95cdd2032df)
<br>
##### Use of tkcon to find mask layer description
![mask layer description](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/0e26d070-35d3-4844-bbf7-9c0e10a4b34a)
##### Use of "what" command to find layer of vertical metal(vmetal) and horizontal metal(hmetal)
![use of what](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/f40b5f46-4ad5-4b8e-a156-187438c94b02)


#### Run Placement and open in Magic
                    % run_placement

                    # Command to run floorplan in Magic
            >> magic -T/home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

##### Figure: Design stats
![design stats](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/6d926603-dd09-48d4-b0fe-b0ef4e3eaf0a) <br><br>
##### Placement of cells in Magic 
![placement](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/b9ee4ca6-6ddc-4ef0-8993-70266e9dd1ae) <br><br>
##### Zoomed in to view the placed standard cells
![zoomed ver](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/a4f0aeac-7650-4912-8006-13a6aa8d689f)
<br><br>
## [ DAY-3 (Design library cell using Magic Layout and ngspice characterization)](https://github.com/sagainfinite/vsdcourse_indrani?tab=readme-ov-file#DAY-3) <br>
#### PART 1: Clone the git of standard cell (Inverter)
#### PART 2: Extraction to Spice in Magic Tool
#### PART 3: Detect DRC issues and fix them
<br><br>
### PART 1: Clone the git of standard cell (Inverter) <br>

       # Cloning the repo with inverter design
      >> git clone https://github.com/nickson-jose/vsdstdcelldesign
      >> cd vsdstdcelldesign

      # Make a copy of the magic file for ease of access
      >> cp /home/vsduser/Desktop/work/tools/openlane_workign_dir/pdks/sky130A/libs.tech/magic/sky130A.tech
      >>ls -ltr

      # Open inverter layout in Magic Tool
      >> magic -T sky130A.tech sky130_inv.mag &
      <br>
##### Figure: Command to open Magic Tool
![command to open magic](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/a8585df1-c7ca-457e-b5cf-f727660bfc12)
<br>
##### Figure: Inverter in Magic
![inv in magic](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/8857b3e2-2d7f-4e56-a9cc-847def67a1e1)
<br>
##### Figure: Nmos layer 
![nmos layer](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/1d2714c0-fcde-41be-83e2-96537e316aa7)
<br><br>
### PART 2: Extraction to Spice in Magic Tool
     # Extracting to ".ext" formatting
     >> extract all

     # Convert the extracted to spice
     >> ext2spice cthresh 0 rthresh 0
     >> ext2spice
![extract to spice](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/30b81db4-d1ae-4afb-bc8c-1ba07e3ccdd1)
<br>
##### Figure: Cloned Inverter
![cloned inv](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/30d4e67a-8399-4944-8122-4f950a1e61f1)
<br>
##### Figure: Spice files to describe pshort and nshort
![spice p and n](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/8a3f23db-08db-4032-92a3-3ed4196a97c7)
##### Figure: Inside pshort lib file
![inside pshort](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/a38892ea-33a5-4298-9b82-3a0c14c6a078)
<br><br>
#### Editing inside ngspice 
##### Figure: Before editing
![before](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/a94bf4d0-4ca6-43c4-b3d3-557111a63047)
      # Enter the following new commands and description
      >> .include ./libs/pshort.lib
      >> .include ./libs/nshort.lib
      >> //.subckt sky130_inv 'A Y VPWR VGND
      >>  M1000 Y A VGND VGND nshort_model.0 ad=1.44n pd=0.152m as=1.37n ps=0.148m w=35 l=23
      >>  M1001 Y A VPWR VPWR pshort_model.0 ad=1.44n pd=0.152m as=1.52n ps=0.156m w=37 l=23
      >>  VDD VPWR 0 3.3V
      >>  VSS VGND O OV
      >> Va A VGND PULSE(OV 3.3V 0 0.1ns 0.1ns 2ns 4ns)
      >> CO Y A 0.0754f
      >> C1 Y VPWR 0.117f
      >> C2 A VPWR 0.0774f
      >> C3 Y VGND 2f
      >> C4 A VGND 0.45f
      >> C5 VPWR VGND 0.781f
      >> // . ends
      >> .tran 1n 20n
         
         . control
         run
         . endc
         . end
        
##### Figure: After editing
![After](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/dbfac479-d960-4c42-8ead-0e64b3b4f4e6)

#### Calculating the following parameters (in nano sec):
##### > fall time
##### > rise time
##### > rise propogation delay
##### > fall propogation delay

##### Figure: Main plot 
      # command to plot in ngspice
      >> plot y vs time a
![main plot](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/89379f15-e107-4d4a-b441-13f9a754d92a)
<br>

##### Figure: Fall Time = 80% VDD - 20% VDD (during fall (logic '1' to logic '0'))
![fall time](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/a6cd7890-7059-47c6-b1d0-7221ba37ce7b)
<br>
##### Figure: Rise Time = 80% VDD - 20% VDD (during rise (logic '0' to logic '1'))
![rise time](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/5446d139-2e38-499e-8b2a-d3a561b55739)
<br>
##### Figure: Rise Propogation Delay at 50% VDD (during rise)
![rise propogation](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/c14e44d4-85a5-4ea8-9d38-66c257b30e7d)
<br>
##### Figure: Fall propogation delay at 50% VDD (during fall)
![fall propogation](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/b9b90dbd-bc87-4d70-bacc-3577c7308522)
<br>
##### Figure: Temperature Status
![temperature](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/07d1f7af-b0fd-4099-bc19-909fe43df087)
<br><br>
