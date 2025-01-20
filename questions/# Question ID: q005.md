# Question ID: q005

## Category
[Platform Basics/Authoring/Development/Maintenance]

## Question
A devops engineer notices that existing pages are not updated through the package installation. The updated pages are present after deleting the pages that are not updating, & reinstalling the package. What is the source of the problem? 

## Options
A) update mode is set
B) install mode is set 
C) merge mode is set
D) replace mode is set 

## Correct Answer
merge mode is set

## Explanation
- replace: This is the normal behavior. Existing content is replaced completely by the imported content, i.e. is overridden or deleted accordingly.
- merge: Existing content is not modified, i.e. only new content is added and none is deleted or modified. Deprecated, as not handled consistently, use merge_properties instead.
- merge_properties: Existing content is not modified, i.e. only new content is added and none is deleted or modified.
- update: Existing content is updated, new content is added and none is deleted. Deprecated, as not handled consistently, use update_properties instead.
- update_properties: Existing content is updated, new content is added and none is deleted.



## Related Concepts
- https://jackrabbit.apache.org/filevault/filter.html#:~:text=merge_properties%20%3A%20Existing%20content%20is%20not,added%20and%20none%20is%20deleted. 

## Tags
# # #

## Difficulty
[Easy/Medium/Hard]

## Notes
Maximum tar file size is 256 so in can not be increased to 512 anyway