# GigE Camera Simulator

This is a GigE camera simulator written in C#.

## How to run
- First install Dotnet 9.0
- Then run the following commands from project's root folder:
```bash
git clone git@github.com:qvops/GigE-Cam-Simulator.git
cd GigE-Cam-Simulator
dotnet run --project src
```

## Functions:
- Discover: answering discovery requests
- Software Trigger: Provide images for software trigger requests.

## How it works:
The simulator is a state machine that provides access to a simulated camera memory. A GigE Vision client can read and write to this memory/register to control the simulated camera. 
When the simulator starts, it uses the "data/memory.xml" file to initially write default values to the memory (e.g. "Manufacturer_name" or "image-width"). 
In addition, the camera description file "data/camera.xml" is written into the memory at start-up, which contains the functional description of the camera.

When the client writes to register 0x30c, an image is sent to the client.

## To configure your simulator camera, you must:
- edit the file "data/memory.xml" to set the memory values.
- edit "data/camera.xml" if you want to change the camera functions
- edit "program.cs" to add logic to the camera and provide image files

## Specification
see:
https://www.visiononline.org/userAssets/aiaUploads/File/GigE_Vision_Specification_2-0-03.pdf

## Inspired by
- [Aravis](https://github.com/AravisProject/aravis)
- [tualo / gigecamera-simulator](https://github.com/tualo/gigecamera-simulator)

See also:
- https://github.com/Strongc/VirtualGEVCam
