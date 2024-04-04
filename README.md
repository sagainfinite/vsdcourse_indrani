# VSD SOC Design using OpenLANE

### Day-wise Checklist
- [x] [**DAY - 1**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-1) <br>
- [x] [**DAY - 2**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-2) <br>
- [ ] [**DAY - 3**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-3) <br>
- [ ] [**DAY - 4**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-4) <br>
- [ ] [**DAY - 5**](https://github.com/sagainfinite/vsdcourse_indrani/blob/main/README.md#DAY-5) <br>
<br>
_Author: Indrani Aekabote_

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

## [ DAY-2 (Determine Die Area and floorplan and placement in Magic)](https://github.com/sagainfinite/vsdcourse_indrani?tab=readme-ov-file#DAY-2) <br>
#### PART 1: Die Area 
#### PART 2: Floorplan
#### PART 3: PLacement

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
