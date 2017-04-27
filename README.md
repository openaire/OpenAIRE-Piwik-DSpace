# OpenAIRE Piwik plugin for DSpace v.6

DSpace implementation for OpenAIRE Piwik tracking.

    Provide usage data for OpenAIRE usage statistics.
    Contact dpierrakos@gmail.com to request OpenAIRE Piwik Site ID
## Download patch

[Patch](https://raw.githubusercontent.com/dimitrispie/OpenAIRE-Piwik-DSpace/master/piwik-openaire-dspace6.diff)

## Installation
```bash
git apply --check patchfile
```
```bash
git apply --whitespace=nowarn --reject patchfile`
```
Change site ID in oapiwik.cfg
```bash
mvn package
```
```bash
ant update
```
