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

========================
WITH HOMEBREW (EASIER)
========================

The following instructions can be read on: https://treehouse.github.io/installation-guides/mac/mongo-mac.html

Install and Run MongoDB with Homebrew
Open the Terminal app and type brew update.
After updating Homebrew brew install mongodb
After downloading Mongo, create the “db” directory. This is where the Mongo data files will live. You can create the directory in the default location by running mkdir -p /data/db
Make sure that the /data/db directory has the right permissions by running

> sudo chown -R `id -un` /data/db
> # Enter your password
Run the Mongo daemon, in one of your terminal windows run mongod. This should start the Mongo server.
Run the Mongo shell, with the Mongo daemon running in one terminal, type mongo in another terminal window. This will run the Mongo shell which is an application to access data in MongoDB.
To exit the Mongo shell run quit()
To stop the Mongo daemon hit ctrl-c

I found there were some errors, which needed to be resolved:

Error: The `brew link` step did not complete successfully
The formula built, but is not symlinked into /usr/local
Could not symlink bin/bsondump
Target /usr/local/bin/bsondump
already exists. You may want to remove it:
  rm '/usr/local/bin/bsondump'

To force the link and overwrite all conflicting files:
  brew link --overwrite mongodb

To list all files that would be deleted:
  brew link --overwrite --dry-run mongodb

Possible conflicting files are:
/usr/local/bin/bsondump

So I opted to force the link and overwrite all conflicting files. Subsequently, running mongod in one terminal and then mongo in another worked.

