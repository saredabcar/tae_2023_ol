#OpenLANE

## Interactive Flow

### 1. Starting the OpenLANE Environment

OpenLANE uses Docker to create a reproducible environment for your projects. To access this environment execute the following:

```yaml 
cd $OPENLANE_ROOT
make mount
```

!!!example
	
	![Mounting Docker](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/mounting_docker.png)

### 2. Running the flow

The entry point for OpenLane is the `./flow.tcl` script. 
In order to start interactive sessions in automatic mode, you need to execute the following command:

```yaml
./flow.tcl -interactive
```

!!!example
	
	![Running Interactive flow](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/running_interactive_flow.png)
	
Once in OpenLANE environment, you have to source the openlane package and initialize your design:

```yaml
package require openlane
```

`prep -design <design_name> -tag <tag_name>`

!!!example
	
	![init_interactive_des](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/init_interactive_design.png)
	
#### Interactive flow commands

When the design is correctly initialized, you can start running the interactive flow commands as the following sequence:

```yaml
run_synthesis
```

```yaml
run_floorplan
```

```yaml
run_placement
```

```yaml
run_cts
```

```yaml
run_routing
```

`write_powered_verilog -output_def ./designs/<design_name>/runs/<run_tag>/results/routing/wpv_<design_name>.def -output_pnl ./designs/<design_name>/runs/<run_tag>/results/routing/wpv_<design_name>.pnl.v -output_nl ./designs/<design_name>/runs/<run_tag>/results/routing/wpv_<design_name>.nl.v`

```yaml
run_magic
```

```yaml
run_magic_spice_export
```

```yaml
run_magic_drc
```

```yaml
run_lvs
```

```yaml
run_antenna_check
```

### 3. Interrupted flow

OpenLANE allows you to return to a previous ‘on going’ flow in interactive mode.

!!!example
	Assuming you have run until _`placement`_ step, and after a while you want to continue that particular run, you must mount docker and execute `flow.tcl` script with the run name you previously assigned to it and continue executing the flow.

	![prep_interrupted](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/prep_interrupted.png)
	
	![exit_interrupted](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/exit_interrupted.png)

	![ret_interrupted](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/ret_interrupted.png)

