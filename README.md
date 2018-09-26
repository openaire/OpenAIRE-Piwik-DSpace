# OpenAIRE Piwik plugin for DSpace

DSpace implementation for OpenAIRE Piwik tracking.

    Tracks usage activity for OpenAIRE usage statistics service.
    Contact dpierrakos@gmail.com to request an OpenAIRE Piwik Site ID and an Authentication Token.

<strong>NOTE:</strong> The patches require the source release of a DSpace to be validated and recompiled.

## Download patch

[Patch for DSpace v.4](https://raw.githubusercontent.com/openaire/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace4.diff)
					   
[Patch for DSpace v.5](https://raw.githubusercontent.com/openaire/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace5.diff)

[Patch for DSpace v.6](https://raw.githubusercontent.com/openaire/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace6.diff)

## Validate and Apply the patch

Follow the steps below:
- Place and optionally rename, the downloaded <strong>patchfile</strong> in the source folder of Dspace installation, i.e. <strong>[dspace-source]/dspace/</strong>
- Change the working directory to this folder.
- Run the following command to validate the <strong>patchfile</strong>.

```bash
git apply --check patchfile
```
- Run the following command to apply the patch.

```bash
git apply --whitespace=nowarn --reject patchfile
```

## Configure tracker parameters
- Change Piwik site ID and Piwik Authentication Token in <strong>oapiwik.cfg</strong>, located in <strong>[dspace-source]/dspace/config/modules</strong>
- Optionally specify the number of bytes in IP Address for IP Anonymization (for supported versions only).
- Enable (<strong>true</strong>) or disable (<strong>false</strong>) the tracker. Default value is <strong>true</strong>.

## Build and Deploy the patch
Run the following commands to rebuild and deploy the tracker in DSpace.

```bash
mvn clean package
```
Change the working directory to <strong>[dspace-source]/dspace/target/dspace-installer</strong>

```bash
ant update
```

## Configure SQLite DB for missing requests
In case of Matomo connectivity issues an SQLite Database is used to store missing requests. 
- To create the DB:
	
```bash
[dspace.dir]/bin/dspace resend-to-matomo -create
```
- Any time during the day, or once a week, execute the following command to submit the missing requests to Matomo

```bash
[dspace.dir]/bin/dspace resend-to-matomo -retry
```
 
 -  After sending the missing requests, execute the following command to delete submitted requests from the DB

 ```bash
 [dspace.dir]/bin/dspace resend-to-matomo -delete
```
## If Matomo patches are already installed, please download the following patches with the SQLite functionality

[Updated Patch with SQLite for DSpace v.4](https://raw.githubusercontent.com/openaire/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace4-sqlite-update.diff)

[Updated Patch with SQLite for DSpace v.5](https://raw.githubusercontent.com/openaire/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace5-sqlite-update.diff)

[Updated Patch with SQLite for DSpace v.6](https://raw.githubusercontent.com/openaire/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace6-sqlite-update.diff)

## Restart Tomcat server
Tomcat server restart is required to apply the changes.
