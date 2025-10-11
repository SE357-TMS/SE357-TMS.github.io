# Activity Rules

- Write diagram in activity PlantUML syntax
-
- There are 2 "swimlanes", which the first is what I will tell you later (and alias the name yourself), second is System (short for S).
- The system swimlane |S| only represents the actions: display **_, verify _**, update **_, notify _**.
- Every node in the diagram must be connected to another node and be connected from another node, except for the start node and the end node.
- The names of action nodes should follow the structure: verb + noun / noun phrase. Condition nodes should also use verbs with meanings such as check, verify, etc.
- Only use if - else (not if - else if) and repeat - repeat while statements. The branch labels should also be written with an uppercase first letter, such as Yes, No, or Valid, Invalid.
- The start node and end node must always be in the actor’s swimlane.
- The first action can be select function \_\_\_ (similar or identical to the use case name, for example, select function ABC...).
- The final action can be confirm notification.
  For example, if the system displays a success message, the customer confirms the success, or confirms the end of the use case (end of the function), and then the end node follows.
- There must be only one start node and one end node; therefore, if any exceptions occur, they should be represented as a repeat - repeat while loop.
- With the generic use case (filename is same as it's parent folder name), you should follow `docs/docs/activity/view-product/view-product.md`,... You must exclude the generic in the if sections, and short in alphabet order.
- With the search use case (filename is like for search use case), you should follow `docs/docs/activity/view-product/search-product.md`,...
- With other CRUD use case, you should follow `docs/docs/activity/view-product/view-product-detail.md`, `docs/docs/activity/view-product/add-comment-to-review.md`,...
- The folder which only has 1 file in that folder, same filename as the folder is a special activity. It isn't generic use case, but a single use case.
