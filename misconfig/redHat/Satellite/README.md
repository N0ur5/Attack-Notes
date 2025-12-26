# Red Hat Satellite

URL: [https://www.redhat.com/en/technologies/management/satellite](https://www.redhat.com/en/technologies/management/satellite)

Description: Red Hat Satellite is used to manage Red Hat Linux Enterprise environments. 

Attack Notes/Observations: 
* The `/pub/` directory can be a gold mine. It is often set intentionally with Directory Listing enabled.
* Different `.ks` files (kickstart files) may have hardcoded creds or configs specific to the org.
* Inspect any/all readable files though as any could potentially have been modified to the orgs needs.


Files:
* `satellitePubDir.yaml` - Nuclei detection template for the exposure. 
