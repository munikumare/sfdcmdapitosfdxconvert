# sfdcmdapitosfdxconvert

Retrieve unpackaged metadata from Developer org and convert it into sfdx project format and create scratch org from it and push the changes to scratch org

Authenticate Developer Org with sfdx (use your developer account)
sfdx force:auth:web:login -d -a Developer org

Metadata Retrieve from (Developer Org) - Required Package.xml
sfdx force:mdapi:retrieve -s -r ./unpackaged -u munikumare@gmail.com -k unpackaged/package.xml

Create SFDX Project structure 
sfdx force:project:create -n mdapi

Convert Metadata API format to SFDX format - Run the command from the SFDX Project folder
sfdx force:mdapi:convert -r ../unpackaged/unpackaged 

Create Scratch org from the Developer Org / DevHub - Run the command from the SFDX Project folder
sfdx force:org:create -s -f config/project-scratch-def.json -a "Dev1"

Push the sfdx changes to newly created scratch org
sfdx force:source:push -u Dev1
