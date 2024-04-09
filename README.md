# VSD SOC Design using OpenLANE

### Day-wise Checklist
- [x] [**DAY - 1 Inception of open-source EDA, OpenLANE and Sky130 PDK**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-1) <br>
- [x] [**DAY - 2 Good floorplan vs bad floorplan and introduction to library cells**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-2) <br>
- [x] [**DAY - 3 Design library cell using Magic Layout and ngspice characterization**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-3) <br>
- [x] [**DAY - 4 Pre-layout timing analysis and importance of good clock tree**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-4) <br>
- [ ] [**DAY - 5 Final steps for RTL2GDS using tritonRoute and openSTA**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-5) <br>
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
<br>
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
      Given: VDD = 3.3V 
      20% VDD = 0.66V
      80% VDD = 2.64V
      50% VDD = 1.65V
      
##### Figure: Main plot 
      # command to plot in ngspice
      >> plot y vs time a
![main plot](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/89379f15-e107-4d4a-b441-13f9a754d92a)
<br>

##### Figure: Fall Time = 80% VDD - 20% VDD (during fall (logic '1' to logic '0'))
![fall time](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/a6cd7890-7059-47c6-b1d0-7221ba37ce7b)
       <br> Fall Time = 0.04247 X 10 ^-9 
<br>

##### Figure: Rise Time = 80% VDD - 20% VDD (during rise (logic '0' to logic '1'))
        <br> Rise time = 0.06104 X 10 ^-9 
![rise time](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/5446d139-2e38-499e-8b2a-d3a561b55739)
<br>
##### Figure: Rise Propogation Delay at 50% VDD (during rise)
          <br> Rise propogation delay = 0.05698 X 10 ^-9 
![rise propogation](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/c14e44d4-85a5-4ea8-9d38-66c257b30e7d)
<br>
##### Figure: Fall propogation delay at 50% VDD (during fall)
          <br> Fall propogation delay = 0.02533 X 10 ^-9 
![fall propogation](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/b9b90dbd-bc87-4d70-bacc-3577c7308522)
<br>
##### Figure: Temperature Status
![temperature](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/07d1f7af-b0fd-4099-bc19-909fe43df087)
<br><br><br>
### PART 3: Detect DRC issues and fix them
 We first download the files from opencircuitdesign.com and then verify the rules mentioned in the SkyWater 130 Periphery RUle tab.
       Link for the Periphery Rules: (https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html#rules-periphery--page-root)
##### Figure: List of Periphery Rules
![list of periphery rules](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/77f17fef-fd4c-4a44-b963-0755eaaa90b5)
<br>
    # Commands to load and extract DRC lab files
    
    >> cd
    >> wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
    >> tar xfz drc_tests.tgz
    >> cd drc_tests
    >> ls -al
    >> gvim .magicrc
    >> magic -d XR 
    
##### Figure: Loading the files
![load the files](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/9d6ff888-d0d2-4b26-ba5e-2279183b359d)
<br>
##### Figure: Extracting the compressed files
![extract the files](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/8c54150e-6f30-45a8-9aed-20ca8650d51f)
<br>
##### Figure: Files under drc_tests
![files under drc_tests](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/3cda4b40-987a-4948-9613-8dc9f2473347)
<br>
##### Figure: Work on the .magicrc file
![work on  magicrc](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/9a1f91e9-1575-4234-93f3-e8ff6ef1ce2e)
<br>
##### Figure: Inside .magicrc
![file  magicrc](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/2ce26c32-9478-403c-b9a8-6987fb0df3da)
<br>
##### Figure: Open the metal3 layer
![open metal3 layer](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/6e8138db-e811-44b6-9920-603b920f6b52)
<br>
##### Figure: Met3 contact cuts
![m3 contact cuts](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/671ed87a-9f03-4b5b-bf9a-bf2b4e67befb)
<br>
##### Figure: Metal3 Periphery Rules
![met3 periphery rules](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/c55253e5-dbe1-4e2b-9ac7-076697f9dbe8)
<br><br>
### 1. Detecting poly.9 drc and fix it
##### Figure: Loading poly layer
![load poly](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/39725963-14e8-4c73-b277-8f200cafad79)
<br>
##### Figure: Dimensions of missing poly
![dim of missing poly](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/d102146e-508a-404f-8d40-0129feab794d)
<br>
##### Figure: Poly.9 periphery rules minimum requirements
![poly 9 constraint req](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/916ac2fc-f5ca-490a-a6a9-2a41cf87b2ff)
<br>
##### Figure: Make changes in sky130A.tech file 
1. *nsd to allpolynonres
![nsd to allpoly](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/64dc38d5-cbc1-4d77-ade3-52a75a794ebf)
<br>
2. alldiff to allpolynonres

![alldiff to allpoly](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/07b89ef5-a642-4dc2-a115-1567459b051a)
<br>
##### Figure: Fixed poly.9
![fixed poly 9](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/1e6def4c-69ce-4932-8da6-bd3bc79f2e92)
<br>
##### Figure: Editing "alldiff" to "allpolynonres" 
![alldiff to allpoly](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/684bec87-503d-4f9b-ba0d-16e34f35047e)
<br>
##### Figure: Editing " *nsd" to "allpolynonres" 
![nsd to allpoly](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/ba91d4a8-4429-423d-91fe-03e0a2cfbbdf)
<br>
##### Figure: Fixed the poly.9 drc error
![fixed poly 9](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/390cb4c5-0a81-4d14-90cc-4070c2d63689)
<br><br>
##### Figure: Check for _drc why_ 
![check for drc why](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/e93c3373-03dc-4e9a-a3d1-c952eb5f8131)
<br><br><br>
### 2. Detect and fix NWELL using templayer and assigning variants
<br>

##### Figure: NWELL is loaded on Magic 
      # Command to load NWELL
      
      >> load nwell
      >> cif ostyle drc
      >> cif see dnwell_shrink
      >> feed clear
      >> cif see nwell_missing
      >> feed clear 
![nwell tkcon](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/e067b632-c7ae-4225-b4b5-8bcb444e18f5)
![nwell before](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/1a4236ac-5a74-4876-a3c9-aa49710cbd28)
<br>
##### Figure: Nwell rules in Periphery Rules under nwell.-
![nwell rules 4 and 5](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/b08c000a-796d-4b29-8310-c16fdc378515)
<br>

##### Figure: Description of "templayer" in sky130A.tech
      # Command to open sky130A.tech under drc_tests
      >> vi sky130A.tech
![templayer bfr](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/04e2e2ca-5268-44a2-8fd1-f4e8520a2c16)
<br><br>
##### Figure: Adding/Editing dnwell
![addign dnwell](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/d9d55fed-4228-4351-ab4f-f48aa02a141e)
<br><br>
##### Figure: Adding variants so as to not slow down Magic Tool
![adding variants](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/73121b26-2483-445b-b356-018b852a4404)
<br><br>
##### Figure: NWELL _tkcon.tcl_ after the above changes
![nwell tkcon after](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/1e4c3296-c162-458a-b104-3f04cfdbf98b)
<br><br>
##### Figure: NWELL after running drc check
![nwell after](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/b74d355d-de49-4b76-86c5-cf7161d723a2)
<br><br><br>
## [ DAY-4 (Pre-layout timing analysis and importance of good clock tree)](https://github.com/sagainfinite/vsdcourse_indrani?tab=readme-ov-file#DAY-4) <br>
#### PART 1: Lab session to configure synthesis settings and fix slack and include custom cell - sky130_inv-ind
#### PART 2: Lab session to configure OpenSTA for post-synthsis timing analysis
#### PART 3: Lab session to run CTS in TritonCTS
#### PART 4: Timing analysis with real clocks in openSTA
<br><br>

### PART 1: Configuring synthesis settings and fix slack then include custom cell - sky130_inv-ind
#### 1. Magic file to standard LEF file <br>
##### Figure: Layers with their co-ordinates in description of _tracks.info_
![layers description](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/e97e058b-230a-4e39-b407-a273e54afbed)
<br><br>
##### Figure: Find how the _grid arguments_ are given
![grid args ](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/f4c6a350-2267-44c6-8dc9-9cb30e5df761)
<br><br>
##### Figure: Give the values as found in description 
![give grid values](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/58026263-3366-49b5-9106-c0ea953b0f6d)
<br><br>
##### Figure: Intersection of Grids in pins _A_ and _Y_
![intersection of grids](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/48229ed4-abfa-4a4b-ba6f-99df7217ac4b)
<br><br>
##### Figure: To specify pins in the design:
      Goto---> Edit-->text
![specifying pins](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/c4cfb696-0626-40a3-9f43-a98a375ea8a1)
<br><br>
##### Figure: Create custom cell _sky130_inv-ind_
    # Command to save the file name
    >> save sky130_inv-ind.mag
    # Check the layout of the custom inverter created
    >> magic -T sky130A.tech sky130_inv-ind.mag &

![creating sky130_inv-ind](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/739c5f61-e68a-48cd-acf7-d568133627d7)
<br><br>
##### Figure: Convert it to LEF format
    # Command to write LEF
    >> left write
![cmd lef write](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/377551b6-9ab4-49ca-be1b-c9f6b6c3cb8a)
<br><br>
##### Figure: Check in directory to find LEF file is created
![lef file created](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/83e98c51-b679-4336-81e3-b0ebfe7c4e9c)
<br><br>
##### Figure: Description of _sky130_inv-ind
![desc of sky130_inv-ind](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/27b88629-b080-449b-afa5-60ba4ec4ddb9)
<br><br>
##### Figure: Description of pin _A_
![pin A in sky130_inv-ind](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/b5ca39b4-80b1-4aa7-93c0-337f84e1b9db)
<br><br>
##### Figure: Make a copy in _src_ under _designs/picorv32a_ directory
![making a copy in src](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/eef3cf8f-965f-4aa1-9bef-97755da7b225)
<br><br>
##### Figure: Opening _config.tcl_ file
![open config tcl](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/c418d77c-1719-4220-ae13-9e65f5f96243)
<br><br>
    # Commands to add in the config.tcl file as shown in figure
    
    >> set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
    >> set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
    >> set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
    >> set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
    >>set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
![config tcl](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/ec1ec5a7-f714-46cc-8a6d-abd35d63eb66)
<br><br>
<br><br><br>
#### 2. Configure Synthesis settings and fix slack <br>
##### Figure: Overwriting an existing runs file 
    # Command to invoke openlane

    >> cd vsduser/Desktop/work/tools/openlane_working_dir/openlane
    >> docker
    >> ./flow.tcl -interactive
    >> package require openlane 0.9
    # Usinf an existing file in runs directory
    
    >> prep -design picorv32a -tag 03-04_05-18 -overwrite
    >> set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
    >> add_lefs -src $lefs
    >> run_synthesis
![overwriting on existing runs file](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/96814846-244d-4291-9653-c36753b1a270)
<br><br>
##### Figure: Chip Area (before synthesis tweaks)
![chip area bfr](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/0f22f7fc-133e-43e4-93d4-1468374cf1a1)
<br><br>
![wns and tns slack](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/54f590ab-0e19-491e-ab74-65dad03a34bc)
<br><br>
##### Figure: Making edits to the following parameters
![readme in configurations](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/83ce2e86-3ec2-40f2-b52d-db6f8ca02565)
<br><br>
##### Figure: Run the synthesis
![run new synth settings](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/62c0d78d-3232-47be-bd22-8d31646a33a1)
<br><br>
##### Figure: Description of custom cell sky130_inv-ind
![desc of sky130_inv-ind](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/27b88629-b080-449b-afa5-60ba4ec4ddb9)
<br><br>
##### Figure: Slack value has decreased after _run sythesis_ again
![slack value after](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/04bdac5d-b118-4ff1-8b13-85d3ce55c97e)
<br><br><br>

#### 3. Floorplanning and Placement
      # Command for floorplanning and placement

      >> init_floorplan
      >> place_io
      >> tap_decap_or
      >> run_placement
##### Figure: Placement success
![placement success](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/2ec47caf-1799-4cd6-9ab0-6993ea5e849f) <br><br>
      # Command to run Magic Tool
      
      >> magic -T/home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
![placement](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/a9a50bcc-15f0-440d-ad45-5cb77ff6c63f)
<br><br>
      # To find the custom cell: type in tkcon.tcl window
      
      >> xload sky130_inv-ind
![xload in tkcon](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/351b0d43-bf17-433f-b77a-c8fef830a660)
<br><br>
      # To view all the internal layers
      
      >> expand
##### Figure: View of _sky130_inv-ind_ cell
![sky130_inv-ind cell](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/0ff8a257-fa31-4646-b0e2-33b363fb7088)
<br><br><br>
### PART 2: Lab session to configure OpenSTA for post-synthsis timing analysis
#### After running _run synthesis_ on Openlane
##### Figure: Create a _pre_sta.conf_ file in the directory
      # The directory to create the pre_sta.conf 
      >> /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane
![pre_sta conf file](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/6c58b5e9-1dc8-4bea-9a79-d56fc95a02b3)
<br><br>
##### Figure: Viewing the existing _base.sdc_ file
    # This base.sdc file is present in the path
    >> /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/scripts
![base sdc file](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/93bf21a7-26f6-481b-8b2d-54afcdd08b38)
<br><br>
##### Figure: Change the capacitance load value(in pico farad) to _17.65_
          # This base.sdc file is present in the path
          >> /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign/libs
![capacitance](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/dcd31bbe-bf11-415b-b1ac-398ba5796b28)
<br><br>
##### Figure: Create a _picorv32a.sdc_ file and view its description
        # The directory to create the picorv32a.sdc
        >> /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src
![picorv32a sdc file](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/976dd0f2-b779-43ea-9e80-ab81720a895a)
<br><br>
##### Figure: Description of _typical.sdc_ file
![typical sdc desc](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/a18665b5-a34d-45eb-acc8-89d834a9eadd)
<br><br><br><br>

### PART 3: Lab session to run CTS in TritonCTS
##### Figure: Run sta by invoking OpenSTA
         # Command to invoke sta 
         >> sta pre_sta.conf
![run sta](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/7467d811-8a51-4573-a5d2-d95223c16a62)
<br><br>
##### Figure: Initial slack value (is high, we will try to reduce it)
![slack before](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/18137f26-cfcd-42d7-8e51-1ef9c289fac1)
<br><br>
##### Figure: Slew of the cell _14513_ before upsizing it (upsizing: inturn reduces the slack)
![before upsizing](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/02644fb5-eb5b-41f6-814e-5caa5eeef576)
<br><br>
      # Command to fix slack by upsizing the cell
      >> report_net -connections _14513_

      # Checking syntax of replace_cell
      >> help replace_cell

       # Replacing cell _14513_
       >> replace_cell _14513_ sky130_fd_sc_hd__or2_4

       # Check for the changes in slew rate and slack value
       >> report_checks -fields {net cap slew input_pins} -digits 4

##### Figure: Executing the above commands on cell _14513_
![14513 cell](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/61bb4f1f-386b-44f0-8766-665fbb75e1bc)
<br><br>
##### Figure: Reduced slack
![final slack after P1](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/07e8a3f9-197d-4413-9ba4-487eb26ab106)
<br><br>
##### Figure: After upsizing cell _14513_
![after upsizing](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/0240082a-fc9d-437a-90fd-b24c64d42b35)
<br><br>
##### Figure: _tns_ and _wns_ values after slack reduction
![tns and wns values](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/99681e99-e734-4897-b92a-925f131a65b7)
<br><br>
 ##### Executing the above step on cell _14481_ as well
![14481 cell](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/4d85c4ae-5b48-4d39-b4eb-99fa339de726)
<br><br>
##### Figure: Find the startpoints and endpoints to run the report check
      # Command to run the _report checks_
      >> report_checks -from _29052_ -to _30440_ -through _14513_
![start and end points](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/61367cd9-97b3-4bc3-a0c0-296e3206a8b2)
<br><br>
##### Figure: Final Slack Value reduced considerably to _- 22.79_
![final slack reduced value](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/1bcc2bac-99b6-4643-a305-15f6d28e7fa6)

    Difference in slack value = (initial - final) slack
                              = (- 23.5092 - (- 22.79)) 
                              =  - 0.7192 
##### Figure: Give the permission using command _chmod 755 picorv32a.synthesis.v_ 
![chmod 755 permission](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/9616d544-2bf0-455d-b99f-65cf148574e1)
<br><br>
##### Figure: Execute this to update the verilog file 
      # Command to update the verilog file 
      # syntax --> help filename
      >> write_verilog picorv32a.synthesis.v
![write_verilog and exit](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/585c0a54-d0a0-4fce-9f7a-a3f88cd01bde)
<br><br>
##### Figure: Updated synthesis file _picorv32a.synthesis.v_ 
![updated synth v file](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/225ce33e-9744-4c7d-99ef-ad06945c0214)
<br><br>
##### Figure: Check for the cell _14481_ in the updated verilog file
![cell 14481 found](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/82494606-9cdd-48d7-8d48-006fbe035ec4)
<br><br><br><br>

#### 2. Running CTS in TritonCTS

##### Figure: Run floorplan
        >> run_floorplan
![run_placement](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/5c73bc64-4b73-4a6b-a549-b6c7f996c1eb)
<br><br>
##### Figure: Floorplan success
![placement success](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/8782b034-df74-4fc4-9838-e0196943b216)
<br><br>

##### Figure: Running CTS
![running cts](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/bef3a987-06d1-4aed-816b-95b58dfb7049)
<br><br>
##### Figure: CTS success
![cts success](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/482ed0fb-2e05-477a-95e6-ad7648c87348)
<br><br>
##### Figure: CTS file created in synthesis folder
![cts file in synth folder created (https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/d6726685-eb5e-429e-9661-2b1fb4990d0f)
<br><br>
##### Figure: Description of the _cts.def_ file
![cts def file](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/87ea52d0-38d5-4fee-b10c-56305b9aa2e7)
<br><br>
##### Figure: CTS file inside _less README.md_ 
![inside readme for CTS](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/809ec85e-e8c2-4e43-a974-4de99afcd70c)
<br><br>
##### Figure: View _run_cts_ in .tcl description
![run_cts in tcl desc](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/8ede4c18-8229-432e-ac66-eabf0575bd81)
<br><br>
##### Figure: Find for cts in _command.tcl_
![cts tcl in tcl_cmd](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/2463d007-82c9-42b1-9bd3-31a35ade768f)
<br><br>
##### Figure: Let's find the CTS value for these
![lets find cts values](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/0c62e6b1-1b96-4914-b3ed-56d25fe5081b)
<br><br>
##### Figure: Found the CTS values
![found the cts values](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/f49c158b-763c-4bdc-bf76-0b098c2ffc5d)
<br><br>
##### Figure: Two commands to find the CTS values for _typical.sdc_ 
![same 2 same echo](https://github.com/sagainfinite/vsdcourse_indrani/assets/102749620/38c5e1ad-194d-4333-91bb-58d533bb6dfd)
<br><br>


