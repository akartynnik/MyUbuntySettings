First of all:
    `sudo apt-get remove mysql-workbench`
    `sudo apt-get remove mysql-workbench-data`
    


For 64-bit systems, you can install MySQL Workbench with these commands:

    sudo apt-get update 

    cd /tmp 

    wget http://goo.gl/EUsdLB -O mysql-workbench-amd64.deb 

    sudo dpkg -i --force-depends mysql-workbench-amd64.deb 

    sudo apt-get -f install


In 32-bit systems, enter these commands:

    sudo apt-get update 

    cd /tmp 

    wget http://goo.gl/d7my11 -O mysql-workbench-i386.deb 

    sudo dpkg -i --force-depends mysql-workbench-i386.deb 

    sudo apt-get -f install
