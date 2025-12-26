# Red Hat Satellite

URL: 
* [https://www.redhat.com/en/technologies/management/satellite](https://www.redhat.com/en/technologies/management/satellite)

Description: 
* Red Hat Satellite is used to manage Red Hat Linux Enterprise environments. 

Attack Notes/Observations: 
* The `/pub/` directory can be a gold mine. It is often set intentionally with Directory Listing enabled.
* Different `.ks` files (kickstart files) may have hardcoded creds or configs specific to the org.
* Inspect any/all readable files though as any could potentially have been modified to the orgs needs.
* Extracting credentials or secrets may give you access to SSH or other services on the network as they may have been deployed with exposed configs and never updated afterwards. 


Files:
* `satellitePubDir.yaml` - Nuclei detection template for the exposure. 
