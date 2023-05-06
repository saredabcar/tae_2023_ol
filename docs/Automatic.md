#OpenLANE

##Automatic Flow

### 1. Starting the OpenLANE Environment

OpenLANE uses Docker to create a reproducible environment for your projects. To access this environment execute the following:

```sh 
cd $OPENLANE_ROOT
make mount
```

### 2. Running the flow

The entry point for OpenLane is the `./flow.tcl` script. It is used to run the flow, start interactive sessions, select the configuration and create OpenLane design files.

In order to run the flow in automatic mode, you need to execute the following command:

```sh
./flow.tcl -design <design_name>
```

For a design named `spm` the invocation would look something like this:

```sh
./flow.tcl -design spm
```

