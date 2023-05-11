#OpenLANE

## Complementary Tools

### 1.- openlane_summary
!!!info
	After the OpenLane ASIC flow has finished, you have a lot of files in the `run` directory. This tool helps you to explore statistics and useful information with ease.

#### Installation
1.- Go to eda_tools directory and clone the [openlane_summary repository](https://github.com/mattvenn/openlane_summary)

```yaml
cd ~/eda_tools
```

```yaml
git clone https://github.com/mattvenn/openlane_summary.git
```

2.- Move to tool directory and change to branch mpw8.

```yaml
cd openlane_summary
```

```yaml
git checkout mpw8
```

3.- Add the tool directory to your PATH and source your bashrc.

```yaml
echo "export PATH=\$PATH:\"/home/\$USER/eda_tools/openlane_summary\"" >> ~/.bashrc
```

```yaml
source ~/.bashrc
```

#### Usage

To use the tool execute the tool, run the next command followed by the desired option:

```yaml
summary .py –-design <design_name> --<option1> --<option2>
```

!!!info
	Execute the following to get the options list.

	```yaml
	summary .py –h
	```
!!!info
	A "-1" means that a particular check was not run.

!!!example
	
	```yaml
	summary.py –-design APU --summary 
	```

	```yaml
	summary.py –-design APU --run 0 --full-summary 
	```

	```yaml
	summary.py –-design APU --run 0 --gds 
	```

### 2.- GDS3D (3D Visualizer)

GDS3D is an application that can interpret so called IC layouts and render them in 3D. The program accepts standard GDSII files as input data.

#### Installation

1.- Go to eda_tools directory and clone the [GDS3D repository](https://github.com/trilomix/GDS3D)

```yaml
cd ~/eda_tools
```

```yaml
git clone https://github.com/trilomix/GDS3D.git
```

2.- Add the following alias and source your bashrc.

```yaml
echo "alias gds3d=\"/home/\$USER/eda_tools/GDS3D/linux/GDS3D -p /home/\$USER/eda_tools/GDS3D/techfiles/sky130.txt -i\"" >> ~/.bashrc
```

```yaml
source ~/.bashrc
```

```yaml
cd GDS3D/linux/
```

```yaml
chmod +x ./GDS3D
```

#### Checking installation
A simple way to check this tool has been succesfully installed and ready to be executed, run the following:

```yaml
gds3d
```

The expected output is:

![testing_gds3d](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/testing_gds3d.png)

!!!warning
	If you are getting errors similar to these:
	
	![gds3d_error_1](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/gds3d_error_1.png)

	![gds3d_error_2](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/gds3d_error_2.png)

	Try to solve it running the following sequence of commands:

	```yaml
	sudo apt -y update && sudo apt -y upgrade
	```
	
	```yaml
	sudo apt autoremove -y
	```
	
	```yaml
	sudo apt install -y g++ libc6 libc6-i386 libx11-6:i386 libgl1-mesa-glx libgl1-mesa-dev libgl1-mesa-glx:i386 libglu1-mesa-devel libx11-dev
	```

	!!!success
		Now, try again to execute `gds3d`. Everything should be OK now    :)

	!!!failure
		If the error you get is:
	
		![gds3d_error_3](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/gds_error_3.png)

		There are more questions than answers...  :(

#### Usage
In order to use the GDS3D visualizer, you should have already defined the alias `gds3d` as explained in previous section.
Thereafer you can invoke the tool ass follows:

```yaml
gds3d <file.gds> / <./path/to/file.gds>
```

!!!example
	Assuming the current directory to be `$OPENLANE_ROOT`, the design to view its `GDS` is `APU` and the run tag is `automatic_flow_1`, the command should look something like this:

	```yaml
	gds3d ./designs/APU/runs/automatic_flow_1/results/final/gds/APU.gds
	```

