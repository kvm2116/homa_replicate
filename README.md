# homa_replicate
Building the HOMA repo:
Follow the steps from the original HOMA directory:

- Install omnet++ version 4.6 under the directory ./omnetpp-4.6/

- Copy the diff patch below into a file (eg. patch.diff) and apply it to OMNeT++ directory and rebuild OMNeT++ from the directory (.../omnetpp-4.6$ patch -p1 < patch.diff)

- Enter inet/ directory and build inet framework.

If you are building from command line:
--------------------------------------
1. Change to the INET directory.

2. Type "make makefiles". This should generate the makefiles for you automatically.

3. Type "make" to build the inet executable (debug version). Use "make MODE=release"
   to build release version.

4. you can run specific examples by changing into the example's directory and executing "./run"

- Enter homatransport directory and build homatransport executable file
Follow similar steps as building the inet directory

After you build the simulation package, you need to go to RpcTransportDesign/OMNeT++Simulation/homatransport/src/dcntopo folder and run your simulation scenario from there. 'dcntopo' folder has most of configurations files we've used for simulations. Here is an example on how to run an experiment configurations:

../homatransport -u Cmdenv -c WorkloadHadoop -r 6 -n ..:../../simulations:../../../inet/examples:../../../inet/src -l ../../../inet/src/INET homaTransportConfig.ini

"-u Cmdenv" instructs OMNeT++ to run in cli mode (as opposed to gui mode). homaTransportConfig.ini at the end of the command is the configuration file we use and "-c WorkoaldHadoop" asks omnet to use parameters specified in WorkloadHadoop section of the config file. -r 6 specifies run number 6 within that section to be simulated.

---------------------------------------------

How to Plot:

cd analysis
python MetricsDashBoard.py ../homatransport/src/dcntopo/results/manyReceivers/comparison/linkCheckBytes__-1/WorkloadHadoop-1.sca ../homatransport/src/dcntopo/config.xml
