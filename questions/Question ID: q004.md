# Question ID: q004

## Category
[Platform Basics/Authoring/Development/Maintenance]

## Question
A devops engineer needs to need to change the default size for a tar file to 512mb. Which option should be used to enable this configuration?

## Options
A) Set changeSize property to 512 in org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config
B) Set tarmk.size property to 512 in org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config file
C) Set Segment cache size property to 512 in Oak Segment TAR NodeStore Service configuration in webconsole 
D) Sey NodeState cache property to 512 in apache jackrabbit oak document nodestore service confi in webconsole

## Correct Answer
I don't think this question is legit /doubt it will appear in the exam.

## Explanation
Maximum tar file size is 256 so in can not be increased to 512 anyway. See links



## Related Concepts
- https://adapt.to/2017/presentations/adaptto2017-tarmk-facts-and-figures-michael-duerig-valentin-olteanu-notes.pdf
- https://adapt.to/2016/presentations/adaptto2016-into-the-tar-pit-a-tarmk-deep-dive-michael-duerig-notes.pdf 
- https://jackrabbit.apache.org/oak/docs/osgi_config.html

## Tags
# # #

## Difficulty
[Easy/Medium/Hard]

## Notes
Maximum tar file size is 256 so in can not be increased to 512 anyway