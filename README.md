# Cascade-Circuit-Analyser
Analyses cascade circuits using a .net input file. It generates a .csv output file with impedances, frequencies, voltages and currents. 

Input files contain 3 blocks in this format:

\# define a circuit between \<CIRCUIT> and \</CIRCUIT> delimiters

\# Elements have two node numbers and component value is a 

\# resistance R=1/G (Ohms), a conductance G=1/R (Seimens), an inductance (Henries)

\# or a capacitance (Farads).

\<CIRCUIT>

n1=1 n2=2 R=8.55
n1=2 n2=0 R=141.9
n1=2 n2=3 R=8.55
n1=3 n2=4 L=1.59e-3
n1=4 n2=0 C=3.18e-9
n1=4 n2=0 L=7.96e-6
n1=4 n2=5 C=6.37e-7
n1=5 n2=0 R=150.5
\# components do not have to follow their order in the circuit
n1=6 n2=0 R=150.5
n1=5 n2=6 G=0.02677
\</CIRCUIT>

\# define the terminations between \<TERMS> and \</TERMS> delimiters

\<TERMS>

\# A 5V Thevenin voltage source with RS=50 ohms connected

\# between node 1 and the implicit common (0) node

VT=5 RS=50
\# A 2.5 Amp Norton current source with RS=25 Ohms

\#IN=2.5 RS=25

\#IN=2.5 GS=0.04

\# Load connected between last node (6 in this case) and the implicit common (0)

RL=75
\# Frequency range and number of frequencies to evaluate at. 

Fstart=10.0 Fend=10e+6 Nfreqs=10
\</TERMS>


\# define the outputs between \<OUTPUT> and \</OUTPUT> delimiters

\# Order of parameters defines the order they appear in the columns of the 

\# output file and their units.

\<OUTPUT>

Vin V
Vout V
Iin A
Iout A
Pin W
Zout Ohms
Pout W
Zin Ohms
Av 
Ai
\</OUTPUT>

to run ’Cascade_Circuit_Analyser.py’ on the input file the command line should be
python Cascade_Circuit_Analyser.py "input_file_name".net "output_file_name".csv

