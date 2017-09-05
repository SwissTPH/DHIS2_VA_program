# DHIS2 Demo Setup

It's possible to create a demo version with fake data on an empty DHIS2 instance including the BLOBs which holds fake data about cars. 
To do this, follow these steps:

Import the following metadata files via **DHIS2's Import/Export** app in the following order:

1. Import `demo-setup/metadata/example_organisationUnits_hierarchy.json` .
2. Import `demo-setup/metadata/sex_optionSet.json`  to import the standard Sex optionSet.
3. Import `metadata/1_VA_metadata_ICD-10_optionSet.json` for the ICD-10 optionSet
4. Import `metadata/2_VA_metadata_dataElements.json` for the program's dataElements
5. Import `metadata/3_VA_metadata_program.json` for the program

Create **Verbal Autopsy dummy data**:

6. Change directories with `cd demo-setup/data`
7. Use the script `post_demo_events.py` as follows:

```
usage: python post_demo_events.py --server --username --password --orgunit [--events] 

Create demo data to load into the Verbal Autopsy program

optional arguments:
  -h, --help           show this help message and exit
  --server SERVER      DHIS2 server URL
  --username USERNAME  DHIS2 username
  --password PASSWORD  DHIS2 password
  --events [EVENTS]    Amount of events to generate (default: 1000)
  --orgunit ORGUNIT    OrgUnit UID to register events

```

Example to create 500 events:

```
python post_demo_events.py --server=play.dhis2.org/demo --username=admin --password=district --orgunit=SCVeBskgiK6 --events=500
```