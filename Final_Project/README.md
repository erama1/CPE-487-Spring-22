# **Final Project: Pacman** 

# About
VHDL implementation of retro game Pacman originally created by [atahanyorganci](https://github.com/atahanyorganci/pacman-in-vhdl) on a [Basys 3 development board](https://digilent.com/reference/_media/basys3:basys3_rm.pdf). The game is displayed through VGA port with 800x600 @60Hz resolution with 4-bit colours. It is played using serial terminal with standard WASD controls. Player's highest and current score is displayed on the seven segment display.

We have taken this project and made it functional on a [Nexsys-A7 Board](https://digilent.com/reference/programmable-logic/nexys-a7/reference-manual) by remapping the original contraint file pins to our board.

# Requirements
* **Nexys A7-100T**
* **Vivado 2019.1 Installation**: To set up Vivado, see the [Installing Vivado and Digilent Board Files Tutorial](https://reference.digilentinc.com/vivado/installing-vivado/start).
* **Serial Terminal Emulator**: For more information, see the [Installating and Using a Terminal Emulator Tutorial](https://reference.digilentinc.com/learn/programmable-logic/tutorials/tera-term).
* **MicroUSB Cable:** To connect to serial terminal
* **USB Keyboard:** To use WASD keys to play the game
* **5V external power supply for board:** To power the board

# Board Designs

## Basys3 Pin Mappings (Original)
<img src="https://user-images.githubusercontent.com/45573682/165873479-489dd682-78ca-4340-b811-633724ea3e8a.JPG" alt="Basys3 VGA Pins" title="Basys3 VGA Pins" height="600"> <img src="https://user-images.githubusercontent.com/45573682/165876145-eba6e037-af23-42bd-a075-4b49fe47e3f3.JPG" alt="Basys3 Switch Pins" title="Basys3 Switch Pins" height="600">


## **Nexsys-A7 Pin Mappings** (Updated)
<img src="https://user-images.githubusercontent.com/45573682/165873472-0c0829a8-c2c0-4382-b819-7ff2d260bbc3.JPG" alt="Nexsys-A7 VGA Pins" title="Nexsys VGA Pins" height="600"> <img src="https://user-images.githubusercontent.com/45573682/165876356-bd2aafcf-7489-4db6-8a32-fef03903e1a9.JPG" alt="Nexsys-A7 Switch Pins" title="Nexsys Switch Pins" height="600"> 
