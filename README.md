# OpenAIRE Piwik plugin for DSpace

DSpace implementation for OpenAIRE Piwik tracking.

    Tracks usage activity for OpenAIRE usage statistics service.
    Contact dpierrakos@gmail.com to request an OpenAIRE Piwik Site ID and an Authentication Token.

<strong>NOTE:</strong> The patches require the source release of a DSpace to be validated and recompiled.

## Download patch

[Patch for DSpace v.4](https://raw.githubusercontent.com/dimitrispie/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace4.diff)

## Download patch with optional IP Anonymization

[Patch for DSpace-CRIS v.4](https://raw.githubusercontent.com/dimitrispie/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace4-cris.diff)

[Patch for DSpace v.5](https://raw.githubusercontent.com/dimitrispie/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace5.diff)

[Patch for DSpace v.6](https://raw.githubusercontent.com/dimitrispie/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace6.diff)

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
## Restart Tomcat server
Tomcat server restart is required to apply the changes.
