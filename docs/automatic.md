#OpenLANE

##Automatic Flow

### 1. Starting the OpenLANE Environment

OpenLANE uses Docker to create a reproducible environment for your projects. To access this environment execute the following:

```yaml 
cd $OPENLANE_ROOT
make mount
```

!!!example
	
	![Mounting Docker](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/mounting_docker.png)

### 2. Running the flow

The entry point for OpenLane is the `./flow.tcl` script. It is used to run the flow, start interactive sessions, select the configuration and create OpenLane design files.

In order to run the flow in automatic mode, you need to execute the following command:

```yaml
./flow.tcl -design <design_name>
```
!!!example
	For a design named `spm` the invocation would look something like this:

	```yaml
	./flow.tcl -design spm
	```
	
	With a `tag`...
	```yaml
	./flow.tcl -design spm -tag automatic_flow_1
	```

	![Running automatic flow](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/running_autom_flow.png)
	

### 3. Exit from the Docker environment
Once the flow has finished/failed, automatically you will be taken outof the OpenLANE environment and positioned at Docker container, being able to run another flow or simply go out to your system environment, again by typing: 

```yaml
exit
```

!!!example
	![Exiting docker](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/exit_docker_autom_flow.png)
