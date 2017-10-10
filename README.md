# OpenAIRE Piwik plugin for DSpace

DSpace implementation for OpenAIRE Piwik tracking.

    Provide usage data for OpenAIRE usage statistics.
    Contact dpierrakos@gmail.com to request an OpenAIRE Piwik Site ID and an Authentication Token
## Download patch

[Patch for DSpace v.4](https://raw.githubusercontent.com/dimitrispie/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace4.diff)

## Patches with optional IP Anonymization

[Patch for DSpace-CRIS v.4](https://raw.githubusercontent.com/dimitrispie/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace4-cris.diff)

[Patch for DSpace v.5](https://raw.githubusercontent.com/dimitrispie/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace5.diff)

[Patch for DSpace v.6](https://raw.githubusercontent.com/dimitrispie/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace6.diff)

## Patch Apply
```bash
git apply --check patchfile
```
```bash
git apply --whitespace=nowarn --reject patchfile
```
## oapiwik.cfg parameters
- Change site ID and authentication token in oapiwik.cfg
- For DSpace 5 and DSpace 6 versions, optionally specify the number of bytes in IP Address for IP Anonymization

## Patch Deploy
```bash
mvn package
```
Change to .../dspace/target/dspace-installer

```bash
ant update
```
