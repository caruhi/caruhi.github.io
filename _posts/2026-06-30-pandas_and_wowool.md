---
layout: post
title: "Pandas and Wowool"
date: 2026-06-30
---

Sometimes, interesting facts in your structured data turn out to be unstructured — for example, a column in a CSV file where an analyst has written comments or other information that does not fit the schema.

We will show how easy it is to extract information and enrich your files using Wowool. For this example, we will use Python and the pandas library.

First, define your Wowool pipeline. In this case, we are using the entity-extended domain, which contains food entities.

We define the pipeline as follows:

```

# Wowool pipeline for entity extraction
pipeline = Pipeline(["english",
                    "entity-extended"
        ])
food_entities = ["Food","Drink","Animal"]

```

We then pass the subject column of our dataframe, which contains free text such as:

```
Salmonella in chilled meatballs used in sandwiches from the Netherlands
```

Next, we define a function to extract food entities:

```
def get_food(subject):
    '''
    Extracts food entities from the subject using the Wowool pipeline.
    If a food entity is found, it returns the lemma of the entity in lowercase.
    If no food entity is found, it returns "unknown".
    '''
    doc = pipeline(subject)
    for ent in doc.entities:
        if ent.uri in food_entities:
            return ent.canonical.lower()
    print("missing food:", subject)
    return "unknown"
```

Finally, we apply the function to the dataframe while preserving the original data:

```
rasff_food_serious['food_entity'] = rasff_food_serious['subject'].apply(get_food)

```
