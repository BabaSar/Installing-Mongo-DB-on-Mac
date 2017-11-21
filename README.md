# Installing-Mongo-DB-on-Mac

Install MongoDB Community Edition
1
Download the tar file from the Mongo website. E.g mongodb-osx-ssl-x86_64-3.4.10.tgz

2
Extract the files from the downloaded archive.
For example, from a system shell, you can extract through the tar command:

tar -zxvf mongodb-osx-ssl-x86_64-3.4.10.tgz

3
Copy the extracted archive to the target directory.
Copy the extracted folder to the location from which MongoDB will run.

Copy
mkdir -p mongodb
cp -R -n mongodb-osx-ssl-x86_64-3.4.10/ mongodb

4
Ensure the location of the binaries is in the PATH variable.
The MongoDB binaries are in the bin/ directory of the archive. To ensure that the binaries are in your PATH, you can use the following command. This will copy all the binaries (stuff in the bin folder) into /usr/local/bin. This is because /usr/local/bin/ is always in the PATH variable.

sudo cp Downloads/mongodb/bin/* /usr/local/bin/

Run MongoDB

1
Create the data directory.

Before you start MongoDB for the first time, create the directory to which the mongod process will write data. By default, the mongod process uses the /data/db directory. If you create a directory other than this one, you must specify that directory in the dbpath option when starting the mongod process later in this procedure.

The following example command creates the default /data/db directory:

sudo mkdir -p /data/db

You will need permissions:

sudo chmod 777 /data/db/

2
Run MongoDB.

Use the following command:
mongod

