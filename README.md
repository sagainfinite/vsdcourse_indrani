# VSD SOC Design using OpenLANE

### Day-wise Checklist
- [x] [**DAY - 1 Inception of open-source EDA, OpenLANE and Sky130 PDK**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-1) <br>
- [x] [**DAY - 2 Good floorplan vs bad floorplan and introduction to library cells**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-2) <br>
- [x] [**DAY - 3 Design library cell using Magic Layout and ngspice characterization**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-3) <br>
- [ ] [**DAY - 4 Pre-layout timing analysis and importance of good clock tree**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-4) <br>
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
<br><br>






