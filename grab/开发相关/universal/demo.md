
For new workflows, we integrated verify place and add place together. You can then change the different workflows by changing the task type. 

flag =>
we add a flag to filter different tasks.
we'll add various options based on business requirements.

Let's enter the review page. Currently, Ops needs to review the current results. 


First of all, for this part of the review, if you choose not to agree. Then subsequent forms sections are not shown. It is important to note that OPS can also independently determine whether the data is correct. For other parts, when we select agree, we will automatically fill in the collected data by default. For coordinate auditing, when the form is filled, the map on the right side shows the corresponding marker that can be dragged and dropped. For street auditing, normalized is directly enabled in the current version. The form section is also adjusted for different countries. Different combinations of street names are displayed depending on the country. Here is the image review. Different from the previous verify place, we require ops to review each image, and the background will score according to the image review results. The area code of the phone number will change according to the country, of course, the prefix is only for display.


对于correct 和incorrect只针对于是否需要给给钱

得禁用，disable，collector联动


Ops need to review whether the POI exists. Here we have two options. When 'Disagree' is selected, it means that the current POI does not exist and all subsequent submissions do not require review. Let's select 'Agree' to proceed with subsequent review. It should be noted that Ops mainly use their judgment of data accuracy to determine whether payment should be made to collectors and verifiers. When 'Agree' is selected, the collector's submission will automatically be populated. Each part will take the current reviewer's submission as the final result. For location, after the reviewer enters or auto-fills the coordinates, a marker will be displayed on the map, which the reviewer can drag to find the correct location.

currently,the workflow is the normalization of the 'street'. The data collection section will be assembled according to the address model of different countries and the form below will automatically adjust according to the country. The new workflow requires Ops to review each image. As before, there are several categories of images here. When 'Bad Photo' is selected, you need to select the reason for the error. If you find a review error, you can hit 'Redo' to review again. The form section works as described above. Next is the review of the entire task. When different review types are selected, the reviewer needs to select different submission reasons. Here, we used a new review model, being the 'XXX' and others. That's pretty much all. If anyone has any questions, please feel free to ask.