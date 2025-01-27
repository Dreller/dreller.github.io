---
title: Power Apps - Super Fast Patch()
date: 2025-01-26 11:55 -0500
categories: [Power Apps, Tricks]
tags: [power fx, performance, database, sharepoint]
---

Have you ever been in the situation where you need to `Patch()` multiple SharePoint List Items?  You probably also noticed that using `ForAll()` is looping throuth all items, one by one.

Well, your users have better to do than looking at a frozen screen.

I tried something and surprisingly, it worked.  Depending on the amount of data you want to update, it can considerably reduce the processing time.  In the following example, it's 12x faster when I update all my records.

![Demo](../assets/media/FastPatch.mov)

This is the code behind the *Floor (Fast)* button.
``` 
ClearCollect( 
    RT_COL_DEPARTEMENTS_PATCH,
        AddColumns( 
            Filter( RT_COL_DEPARTMENTS, ID in RT_COL_DEPARTMENTS_SEL ) As Me, 
            PatchResponse, 
                Patch(
                    Departments, 
                    {ID: Me.ID}, 
                    { 'Severed Floor': !(Coalesce( Me.'Severed Floor', false ) ) }
                )
            )
    );
ForAll( RT_COL_DEPARTEMENTS_PATCH As Me, 
    UpdateIf( RT_COL_DEPARTMENTS, ID = Me.ID, { 'Severed Floor': Me.PatchResponse.'Severed Floor' } )
);
```

The magic trick is to add a column in a Collection, set with the result of the `Patch()` function.  All updates are sent to the server at the same time.  You can then retrieve the results locally and update your local collection.
