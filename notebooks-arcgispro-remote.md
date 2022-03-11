# Developing jupyter notebooks...
## ... for ArcGIS Pro Projects...
### ... remotely ...
#### ... from a Mac.

Authors: Jimmy O'Donnell, James Guillochon

2022-02-01

0. If it doesn't exist, you need a file called "config" in the directory "~/.ssh" (on the Mac).

1. Forward ports by adding the following to ~/.ssh/config. Change "win" to whatever you want, and HostName and User to your credentials.

```
Host win
HostName    jodonnell.esri.com
User        jam10413
Port        22
LocalForward    8889 localhost:8888
LocalForward    6007 localhost:6006
```
The first forwarded port is for jupyter, the second for tensorboard.

2. On the Windows machine, open "Python Command Prompt" in the "ArcGIS" folder of Program Files on the Windows machine.

3. Type `conda activate` so that `(base)` is shown in the command prompt.

4. Type `jupyter lab`

5. Access the url shown via the browser on your mac

6. Select the appropriate kernel in the browser. You might need to install ipykernel to access other kernels

Notes:
- You *should* be able to start the Pro environment from another terminal app (e.g. Windows Terminal rather than "ArcGIS > Python Command Prompt"). To do that, you can start it from here: "Program Files\ArcGIS\Pro\bin\Python\Scripts\proenv.bat"
- If you can do all of this but are getting errors creating or saving notebooks, it could be that you don't have permission to write to the location where you started jupyter.
- If `import arcpy` results in the error "The Product License has not been initialized", it could be that you are using Single Use License. This seems to not work. Try switching to a "Named User License".

### Update

As of now, my process is:
0. Mac: Connect to VPN.
1. Mac: Login in to remote desktop.
2. Win: Open Program Files > ArcGIS > Python Command Prompt
3. Win: `cd C:\Projects`
4. Win: `jupyter lab`
5. Mac: ssh to machine in terminal on Mac (`ssh win`; use whatever you typed for "Host" in the "~/.ssh/config" file.)
6. Mac: In browser, go to localhost:8889
