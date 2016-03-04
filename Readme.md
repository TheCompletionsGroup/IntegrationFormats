**The Completions Tool** is able to import completions data from existing completions projects. This allows you to view overall progress of a large project which relies on numerous other completions tools or gain an overview of multiple projects. In order to do this we have described a common format for the various entities common to most completions tools. If you maintain a completions tool then we invite you to implement this standard or, better yet, contribute to it. We love open source formats. 

#General Format Notes

Even though it is 2016 we're resisting the urge to require that files be formatted in JSON. We have chosen to use comma delimited files (CSV) format because it is easily created in tools as diverse as notepad and Excel on any operating system. It is also a file format which is well-known for less technically minded people. 

Files must be encoded using UTF-8 without a BOM.

Where this spec is not explicit it should be assumed that it complies with [RFC 4180](https://tools.ietf.org/html/rfc4180).

##Floating Point Format

Floating point numbers typically use the `.` character to denote the separation between units and decimals: `45.66`. However in some areas, notably Europe, `,` is used instead. This obviously poses issues for comma delimited files. As such `.` is to be used as the decimal separator. Sorry, France, better luck next time.  

##Multiple Lines

Values which span multiple lines are fine and must be wrapped in quotation marks. 

    Episode Number, Name, Plot
    01,"The Cage","The crew of the Enterprise follow a distress signal to the planet Talos IV, where Captain Pike is taken captive by a group of telepathic aliens. The events of this episode are revisited in the Season 1 episodes ""The Menagerie, Parts I and II"".[28]"
    
When quotation marks are required inside a field then they must be escaped using two quotation marks `""`. There is no need to escape commas inside of a field. 

##Dates and Times

All dates and times must be in UTC and must be formatted in accordance with [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) extended format.

**Examples**

    2015-01-15 15:22:01
    2016-12-01

#File Formats

Note: GUIDs are Microsoft style [GUIDs](https://en.wikipedia.org/wiki/Globally_unique_identifier) and must remain consistent from load to load. Thus a tag with ID 21EC2020-3AEA-4069-A2DD-08002B30309D should always have that ID and any item imported with that ID will be assumed to be that tag. 

##Tags
 - CorrolationId: GUID
 - Tag Number: string
 - Description: string
 - CreationDate: date
 - UpdateDate: date
 - Discipline: string

##Systems
 - CorrolationId: GUID
 - Number: string
 - Name: string

##SubSystems
 - CorrolationId: GUID
 - Number: string
 - Name: string

##Tag Scopings
 - CorrolationId: GUID
 - TagId: GUID
 - SubSystemId: GUID
 
##Deficiencies
  - CorrolationId: GUID
  - Name: string
  - Description: string
  - TagId: GUID
  - SystemId: GUID
  - SubSystemId: GUID
  - ContractorResponsible: String
  - CreationDate: GUID
  - ExpectedCompletionDate: Date
  - ActualCompletionDate: Date
  
  Only one of {TagId, SystemId, SubSystemId} needs to be filled out for a deficiency. Use an empty GUID 00000000-0000-0000-0000-000000000000 for fields which are not filled in. 
  
##Checksheets
   - CorrolationId: GUID
   - Number: string
   - Name: string
   - Discipline: string
   - Phase: string
   
##Work Assignments
   - CorrolationId: GUID
   - ChecksheetId: GUID
   - TagId: GUID
  
##Completed Work Assignments
   - CorrolationId: GUID
   - CompletionDate: Date
   - EntryDate: Date
   - CompletingPerson: string
  
##Certificates
   - CorrolationId: GUID
   - Number: string
   - Name: string
   - Discipline: string
   - Phase: string
  
##Completed Certificates
   - CorrolationId: GUID
   - CompletionDate: Date
   - EntryDate: Date
   - CompletingPerson: string
