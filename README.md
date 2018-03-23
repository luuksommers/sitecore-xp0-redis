# Sitecore XP0 Redis Addon

This module adds redis to your XP0 Azure deployment. By default the XP0 installation uses the InProc session provider causing session loss on redeploy. The sitecore redis addon makes use of the bootloader funcionality to add the redis.session to the ConnectionStrings.config.

You can download the sitecore bootloader at [Configure the Bootloader module](https://doc.sitecore.net/cloud/working_with_sitecore_azure_toolkit/deployment/configure_the_bootloader_module_for_a_sitecore_deployment)

Download the Redis.scwdp.zip from the packages folder and upload it to blob.

## Adding snippet for your module

Add the module:
``` JSON
"modules": {
  "value": {
    "items": [
      {
        "name": "redis",
        "templateLink": "addons/redis.json",
        "parameters": {
          "redisMsDeployPackageUrl": "<link to the Redis.scwdp.zip>" 
        }
      },
      {
        "name": "bootloader",
        "templateLink": "addons/bootloader.json",
        "parameters": {
          "msDeployPackageUrl": "<link to the Sitecore.Cloud.Integration.Bootload.wdp.zip>"
        }
      }
    ]
  }
}
```