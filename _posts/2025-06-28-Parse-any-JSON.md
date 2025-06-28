---
title: Parse any JSON
date: 2025-06-28 14:50 -0500
categories: [Power Automate, JSON]
tags: [flow, automate, performance, database, json, data]
---

Parsing JSON in Power Automate is a common task, but the built-in *Parse JSON* action typically requires a predefined schema. This can be limiting when working with dynamic or unpredictable data structures, as any change in the incoming JSON can break your flow or require constant schema updates. In this post, we'll explore how to handle any JSON—regardless of its structure—within Power Automate, allowing your flows to adapt to changing data without being tied to a static schema. Whether you're integrating with APIs, databases, or other services, this approach will help you build more robust and flexible automations.

## Context and Demo
A Power App will send a stringified JSON to the Flow.  The Flow must parse and handle this data regardless of the schema.

The App build the following Object (Record Variable):
```
Set( MyRecord, {
    FirstName: "Buffy", 
    LastName: "Summers"
} );
```

The Flow is set to receive a Text Parameter.
The App calls the Flow with:
```
'Flow-Name'.Run( text: JSON( MyRecord ) );
```

The Flow contains a *Compose* Action (Action Name: Compose Data) with this expression:
```
if( 
    equals( 
        string( 
            json( 
                coalesce( triggerBody()?['text'], '{}' )
            )
        ),
        json( 
            coalesce( triggerBody()?['text'], '{}' )
        )
    ), 
    json( 
        json( 
            coalesce(triggerBody()?['text'], '{}' )
        )
    ),
    json( 
        coalesce(triggerBody()?['text'], '{}' )
    )
)
```

The Flow can now use the JSON properties like that:
```
coalesce( outputs('Compose_Data')?['Name'], '' )
```

With this trick, you don't need to maintain a JSON schema and you can use the same Flow Parameter to feed it with data from the App.