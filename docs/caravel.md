#Caravel

## Harden your designs

### Prerequisites
- Docker
- Python3
- PIP

Check if you have everything already set:

```yaml 
python3 --version; pip --version; docker run hello-world
```


### 1.-Installation

1. Create a 'caravel_suite' directory which will be the root to allocate caravel_user_project:

	```yaml 
	cd ~/eda_tools
	```

	```yaml 
	mkdir caravel_suite
	```
	
	```yaml 
	cd caravel_suite
	```

2. Clone the caravel_user_project repository as `caravel origin`:

	```yaml 
	git clone https://github.com/efabless/caravel_user_project caravel_origin
	```

3. Set the following three variables in your 'bashrc' file, then source it:

	```yaml 
	echo "export OPENLANE_ROOT=\"/home/\$USER/eda_tools/caravel_suite/caravel_origin/dependencies/openlane_src\"" >> ~/.bashrc
	```
	
	```yaml 
	echo "export PDK_ROOT=\"/home/\$USER/eda_tools/caravel_suite/caravel_origin/dependencies/pdks\"" >> ~/.bashrc
	```
	
	```yaml 
	echo "export PDK="sky130A"" >> ~/.bashrc
	```
	
	```yaml 
	source ~/.bashrc
	```

	!!!warning
		Confirm these are the unique variables with it's corresponding name and are actually pointing to the correct path.
	
		```yaml 
		echo $OPENLANE_ROOT && echo $PDK_ROOT && echo $PDK
		```

		![caravel_vars](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/caravel_vars.png)


4. Move to `caravel_origin` directory. Inside file `Makefile`, modify the variable `CARAVEL_LITE` from 1 to 0:

	!!!example
	
		![caravel_lite_var](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/caravel_lite_var.png)


	Go back to your terminal and execute the following command:

	```yaml 
	make setup
	```

	This command will setup your environment by installing the following:

	- The full version of caravel -> ~/..../caravel_origin/
	- Management core for simulation
	- Openlane to harden your design -> ~/..../dependencies/openlane_src/
	- PDKs (sky130A & gf180mcuC) -> ~/..../dependencies/pdks/

	!!!example 
	
		Successfully completed output:

		![make_setup_success](https://raw.githubusercontent.com/saredabcar/tae_2023_ol/main/assets/images/make_setup_success.png)

	!!!info
	
		If there it is any problem with caravel, you can remove it and start again. Go to 'caravel_origin' and run:

		```yaml 
		make uninstall
		```

### 2. Running the flow


