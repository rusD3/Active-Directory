## **Bloodhound**

You can install the ingestor via pip with pip install bloodhound, or by cloning this repository and running python setup.py install, or with pip install .. BloodHound.py requires impacket, ldap3 and dnspython to function.

The installation will add a command line tool bloodhound-python to your PATH

Run it against DC with user credentials
bloodhound-python -d lab.local -u rsmith -p Winter2017 -gc LAB2008DC01.lab.local -c all

cp .zip to machine running BloodHound

neo4j console

./bloodhound

upload .zip file

[Link](https://github.com/fox-it/BloodHound.py)
