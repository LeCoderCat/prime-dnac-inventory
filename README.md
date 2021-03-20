[![published](https://static.production.devnetcloud.com/codeexchange/assets/images/devnet-published.svg)](https://developer.cisco.com/codeexchange/github/repo/LeCoderCat/prime-dnac-inventory)
# prime-dnac-inventory
Example code on how to perform migration of the devices from Prime Infrastructure inventory to import them to DNA Center's inventory.
The files included on this repository contain:

* Python 3 example code on how to convert the csv file created from Prime's inventory export to get it ready to be imported into DNA Center's inventory

## Instructions
The script should be run on the terminal on a device that has python3 and the required python packages installed.
You can find the packages needed listed on the file requirement.txt

### Setting Up to Run the script
Clone and Prep the Environment
    Clone the code repo
    ```bash
    git clone https://github.com/LeCoderCat/prime-dnac-inventory.git
    cd prime-dnac-inventory
    ```
   
### Setup Python Virtual Environment
    1. MacOS or Linux
    python3.6 -m venv venv
    source venv/bin/activate
    pip install -r requirements.txt
        > Note: If on Linux, you will need to install the Python3.6 development files. On CentOS this is done with yum install -y python36u-devel
    2. Windows - recommendation to use git-bash terminal
    py -3 -m venv venv
    source venv/Scripts/activate
    pip install -r requirements-win.txt
        > Note: Creation and activation of a venv in Windows is slightly different.
    
### Infrastructure Resources needed to run the script
First it is required to have Prime Infrastrucuture, with devices added to the inventory. To export the csv with the device list, go to Inventory > Device Management > Network Devices, select the devices and Export Device.
In order to test the file generated by the script and in case you do not have access to a DNA Center, you can use one of DNA Center's sandboxes available at Cisco's DEVNET site. These sandboxes are preconfigured labs with all resources dedicated to you for the duration of the reservation. You have the ability to install your own application and share the lab with other users.

To start using the content of this repo on Cisco DNA Center sandboxes, click [here](https://sandboxdnac.cisco.com/).

    User: devnetuser
    Password: Cisco123!

### How to run the script

To run the script you will first need the generated csv from Prime Infrastruture (Inventory > Device Management > Network Devices, Export Device).

![Export device inventory - Prime Infrastructure](/img/Prime.png)

Once you have it, place the script file and the csv generated from Prime Infrastructure on the same directory. Once that is done, go to the terminal and navigate to that same directory (in this case Desktop):

```bash
CATPIRES-M:~ catpires$ cd Desktop/
CATPIRES-M:Desktop catpires$ 
```
Then, run the script via python3 and indicate the csv filename (please do not include the file extension .csv!):

```bash
CATPIRES-M:Desktop catpires$ python3 convert_csv.py 
Enter the PI generated file name (don't include .csv): devices_3types
Generating line: 1
Generating line: 2
Generating line: 3
Generating line: 4
Generating line: 5
FILE GENERATED: IMPORT_DNAC.csv
CATPIRES-M-W3TB:Desktop catpires$ 
```
The generated file is ready to be uploaded to DNA Center via Inventory > Actions > Inventory > Import Inventory.

![Import device inventory from Prime - DNA Center](/img/DNAC.png)
