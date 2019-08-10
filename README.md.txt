Team:	NeedNoEntity

Instructions to Run:
1. Put the basic_uart.vhdl, encryption.vhdl and decryption.vhdl (present in VHDL directory) in 20140524/makestuff/hdlmake/apps/makestuff/swled/cksum/vhdl/
2. Replace the hdlmake.cfg in 20140524/makestuff/hdlmake/apps/makestuff/swled/cksum/vhdl/ with the given hdlmake_cksum.cfg (rename this to hdlmake.cfg) file (present in Constraints directory)
2. Replace the hdlmake.cfg in 20140524/makestuff/hdlmake/apps/makestuff/swled/templates/fx2all/vhdl/ with the given hdlmake_top.cfg (rename this to hdlmake.cfg) file (present in Constraints directory)
3. Put the network.txt in /home/*user*/20140524/makestuff/apps/flcli/ (Replace *user* with the proper username)
4. Please change in line 39, 63, 64 of main.c the path of network.txt according to the username of the system you are executing in. Replace **** in "/home/****/20140524/makestuff/apps/flcli/network.txt" to the username.
5. Replace the top_level.vhdl in 20140524/makestuff/hdlmake/apps/makestuff/swled/templates/fx2all/vhdl/ with the given top_level.vhdl (present in VHDL directory)
6. Replace the harness.vhdl in 20140524/makestuff/hdlmake/apps/makestuff/swled/templates/ with the given harness.vhdl (present in VHDL directory)
7. Replace the board.ucf 20140524/makestuff/hdlmake/apps/makestuff/swled/templates/fx2all/boards/atlys/ in with the given board.ucf (present in VHDL directory)
8. Put the debouncer.vhdl (present in VHDL directory) in 20140524/makestuff/hdlmake/apps/makestuff/swled/templates/fx2all/vhdl/



NOTE:- executing the script.sh provided in host/ is equivalent to the below sequential exectution except for the command to start the process, cd to the cksum/vhdl and execute the given start command.

The following are terminal commands
9. cd 20140524/makestuff/apps/flcli
10. make deps
11. cd ../../
12. scripts/msget.sh makestuff/hdlmake
13. cd hdlmake/apps
14. cd makestuff/swled/cksum/vhdl
15. "../../../../../bin/hdlmake.py -t ../../templates/fx2all/vhdl -b atlys -p fpga"
16. "../../../../../../apps/flcli/lin.x64/rel/flcli -v 1d50:602b:0002 -i 1443:0007"
17. "../../../../../../apps/flcli/lin.x64/rel/flcli -v 1d50:602b:0002 -p J:D0D2D3D4:fpga.xsvf"



This is the command to start the process described
18. "../../../../../../apps/flcli/lin.x64/rel/flcli -v 1d50:602b:0002 -b -y"


our key is "11001100110011001100110011000001"
our ack1 is "11011011101101111101111101101110"
our ack2 is "11110000111100001111000011110000"
our position is "00100010" (2,2)

our vhdl code communicates in channels 2 and 3.


Note:- The additional folder called libs in host/ is our attempt to use the flReadChannelAsyncAwait and usbBulkCompletionAwait with timeout parameters, this was a partial success and needs us to have knowledge about libusb package. This is just provided as a proof that we tried to use flReadChannelAsyncAwait with timeout, though we are not using it.  
Note:- We used the Feb 20 convention for sending the data on uart.
Note:- Our code deletes the track info if already present in network.txt if the data from fpga came with trackexists as 0, but it does not add entries if trackexists from fpga was 1. 
Note:- For uart communication we can do it by gtkterm or Our code also works for the optional part with a relay host (we have our own python script for the relay computer provided in the main directory)
Note:- We also provided the .xsvf file in fpga/ just in case if there are issues in compiling 

