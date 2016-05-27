# EXT:filereferenceupdatewizard

## Reason for this extension

If you use upgrade your project from 4.x to 6.2, then there is a TceformsUpdateWizard to bring resources (mostly images) from uploads/* into FAL. Unfortunately this wizard is not aware of the possibility to a setting in TCA, which keeps files in fileadmin instead of copying it to uploads-folder.

    ['columns'][field name]['config'] / TYPE: "group"
    internal_type='file_reference'  

If you used this setting, the Wizard throws errors claiming that the images were not found in uploads/*. In 6.2 the old references would not work anymore, since the are expected to be FAL-based.

This wizard expects the page:media field to use **internal_type='file_reference'** and creates FAL-record in sys_file and sys_file_reference for it. The orginal file is kept in fileadmin.


## Usage

Just install the extension in your upgraded project and run the wizard. Tested with 6.2 LTS.
**Beware: there are no further checks yet, it should only be used if you use file_reference for the pages:media field.**
 
## Next steps
 
Since file_reference was not often used and most projects should be on >= 6.2 meanwhile, we probably won't put much effort into this extension. But we could think of:
   
- make it check for other fields using file_reference
- make sure is does no hard to regular fields if it is used against all warnings without having set file_reference 