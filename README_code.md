This README file explains how to run the code interactively with NuSMV on an Ubuntu terminal.

Steps to be followed:

###	Building the model

1. Get into the interactive mode (this takes you to the NuSMV shell prompt - NuSMV>)

	./NuSMV -int

2. Read the model (smv file)

	read_model -i model.smv

3. Instantiate modules and processes

	flatten_hierarchy

4. Build the BDD variables necessary to compile the model into BDD

	encode_variables

5. Compile the flattened hierarchy into BDD

	build_model

###	Simulation

6. Simulate the path of the specification mentioned.

	simualte -k *num*

    Note: The above command simulates *num* states.

7. Trace the path of the simulation

	show_traces -v

    Note: should we mention what -v does?


One line command to run the code and get the entire output including all the possible BDD nodes and a counter example if the specification is false.

	./NuSMV -v 2 model.smv

