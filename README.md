# comV1
some code to do communication at longue distance (the comment is french cuz i don't speak english)


# how does it work? 
1st step : you have to place a processor and a memory bank with the code in the file [hosting_main_server.mlog](https://github.com/nejjahiishaq2008-sketch/comV1/blob/main/hosting_main_server.mlog), it will become the main server all other server and processor 
will have to log to it 

2nd step : now we want server to save and read value with so place a memory cell or a memory bank depending of what you want and bind it to a processor with the code in the file [hosting_server.mlog](https://github.com/nejjahiishaq2008-sketch/comV1/blob/main/hosting_server.mlog) who will host the server for us. You can also add a switch if you want to shutdown the server and add 2 message block for more information (1st will print error and say if it work and the sencond some useless bs for now) 

3rd step : we're almost done, now we have server we need to get access to them for this we will use a processor with the code in the file [server_login.mlog](https://github.com/nejjahiishaq2008-sketch/comV1/blob/main/server_login.mlog) and bind it with at least a memory cell (we can add  2 message block to get error message and now if it work) the memory cell will be used to communicate, here the list of request:
- get the main server com-0 --> 1
- login to a server with his name com-1 --> name of the server then com-0 --> 2
- login to a server with his slot in the main serv com-1 --> the slot then com-0 --> 3
- read a value of the server com-1 -- > the slot to read then com-0 --> 4 and the value will be saved in com-2
- write a value in the server com-2 --> the value to write then com-1 --> the slot to overwrite then com-0 --> 5 the value that has overwrited will be saved in com-3 if you want to use it, just don't write on the slot 0,1,2 of a server these slot are read-only and contain information about the server
- on com-63 there will be error code -1 if the processor can't login to the main server and -2 if it can't connecte to another server (don't forget for reading or writing in a server you need to login to it before otherwise it won't work)

that's all, there's no comunication protocol and for one only to type of server but if you're smart enough you will find a way to use in project
you can also check [the schema](https://github.com/nejjahiishaq2008-sketch/comV1/blob/main/schema/serveur_schema_mindustry.png)

# how to debug ?

in the folder [display](https://github.com/nejjahiishaq2008-sketch/comV1/tree/main/display) you will find 2 files, [server_nav.mlog](https://github.com/nejjahiishaq2008-sketch/comV1/blob/main/display/server_nav.mlog) and [server_nav_command.mlog](https://github.com/nejjahiishaq2008-sketch/comV1/blob/main/display/server_nav.mlog) these code will display on a screen (it can have some issue if the screen is too small) the value that's stored on the server 

to use it you have to place a processor first and to bind him 4 switch and a memory cell and put the code of [server_nav_command.mlog](https://github.com/nejjahiishaq2008-sketch/comV1/blob/main/display/server_nav.mlog)
- the 1st switch is to move up
- the 2nd one is to move down
- the 3rd one is to log to the selected server
- and the last one is to go back to the previous server

then place a second processor, bind it to 3 memory cell and a screen (it will adapt to the size of the screen) and put the code of [server_nav.mlog](https://github.com/nejjahiishaq2008-sketch/comV1/blob/main/display/server_nav.mlog)
- the 1st memory cell is the same memory cell of the command processor
- the 2nd one is for login to the main server
- the last one is used only by this processor 

now the last part, place a processor with the code [server_login.mlog](https://github.com/nejjahiishaq2008-sketch/comV1/blob/main/server_login.mlog)
and bind it with the second memory cell of the previous processor 

when it's done enjoy what you've made 
