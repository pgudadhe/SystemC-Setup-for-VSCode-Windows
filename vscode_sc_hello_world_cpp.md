In this article I will walk through the first SystemC based Hello World project where we will utilize clocking and SC_METHODs.

First include necessary files in your helloworld.cpp:

```bash
#include <iostream>
#include <vector>
#include <string>
#include "systemc.h"


using namespace std;
```

Lets create our first SystemC module called SCHelloWorld. 

```bash
// Basic SC_MODULE with a SC_METHOD
SC_MODULE(SCHelloWorld) 
{
    sc_in<bool> clock; 
    vector<string> msg {"Hello", "SystemC", "World", "from", "VS Code", "via", "Windows", "Subsystem", "for", "Linux"};
    uint32_t count = 0;

    void process() 
    {
        if(count < msg.size())
            std::cout << "Message: " << msg[count] << " at time: " << sc_time_stamp() << std::endl;
        else
            std::cout << "Tick at time: " << sc_time_stamp() << std::endl;

        count++;
    }

    SC_CTOR(SCHelloWorld) 
    {
        SC_METHOD(process);
        sensitive << clock.pos(); 
    }
};
```

We have clock variable where we will link up the clock from sc_main. 
We have a array of Hello World message which we want to display on each clock cycle.
Those are stored in a vector as below:

```bash
 vector<string> msg {"Hello", "SystemC", "World", "from", "VS Code", "via", "Windows", "Subsystem", "for", "Linux"};
```

We created a process() function which will get called every clock cycle to display the next word of the Hello World message.
Our SystemC module constructor looks like this:

```bash
    SC_CTOR(SCHelloWorld) 
    {
        ....
    }
```

Here we want to designate process() as a SC_METHOD which will get called every clock cycle. We can define this by using sensitivity as below:

```bash
        SC_METHOD(process);
        sensitive << clock.pos(); 
```


Now we will create the sc_main() function. In this function we are going to instantiate our first SC_MODULE class, clock. We are going to link the clock with our module and call to start the simulation.

```bash
int sc_main(int argc, char* argv[])
{
    sc_clock clock("clock", 1, SC_NS); // Create a clock signal with 1 ns period

    SCHelloWorld schw_module("SC HelloWorld");
    schw_module.clock(clock);

    sc_start(10, SC_NS); // Run the simulation for 10 ns


   return 0;
}
```

Build this project and run it. It should display the output as below:

```bash
        SystemC 3.0.1-Accellera --- Jul 23 2025 08:22:58
        Copyright (c) 1996-2024 by all Contributors,
        ALL RIGHTS RESERVED

Warning: (W506) illegal characters: SC HelloWorld substituted by SC_HelloWorld
In file: ../../../src/sysc/kernel/sc_object.cpp:244
Message: Hello at time: 0 s
Message: SystemC at time: 0 s
Message: World at time: 1 ns
Message: from at time: 2 ns
Message: VS Code at time: 3 ns
Message: via at time: 4 ns
Message: Windows at time: 5 ns
Message: Subsystem at time: 6 ns
Message: for at time: 7 ns
Message: Linux at time: 8 ns
Tick at time: 9 ns
```

This concludes our SystemC setup via WSL on Winows for VS Code project.

[Home](https://pgudadhe.github.io/)

