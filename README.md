# Evaluating the Danger of Near Earth Orbit Asteroids


## Overview
Asteroids are space debris, believed to be leftover from the early formation of our solar system approximately 4.6 billion years ago. The majority of these objects are found between the orbits of Mars and Jupiter in a belt known as the "main asteroid belt", but they can also be found outside of this belt. A near-Earth object is an asteroid whose orbit passes close to, or crosses, Earth's orbit. 
## Problem Statement
In 2021, NASA spent roughly $327 million dollars on a project known as DART - Double Asteroid Redirection Test - which was an effort to evaluate protecting Earth from potentially deadly objects by deliberately crashing a spaceborn vessel into an asteroid in hopes of altering its trajectory. Given the immense cost of redirecting one of these objects, a way to determine which objects are likely to pose a hazard to us would be a prudent move towards being as efficient as possible with these ventures. There are 1,303,181 *known* asteroids in our solar system, so we need to train a machine learning model to classify these objects as hazardous or not based on the data that is available from NASA instruments and their open API. If successful, this model could be deployed to ingest data live from the API and provide a continuous monitoring system that could alert us to new threats.

## Data Sources
For this project, I am working with a dataset of near earth objects sourced from [Kaggle](https://www.kaggle.com/datasets/sameepvani/nasa-nearest-earth-objects?resource=download&select=neo_v2.csv), which was originally sourced (in part or in full) from the [NEO Earth Close Approaches API](https://cneos.jpl.nasa.gov/ca/). This data set has 90,837 approaches for 27,423 unique objects from 1900 to 2021.

This data set contains the following features:
- **Object ID**\* - A uniqe ID given to the object by NASA
- **Object Name**\* - A unique name given to the object by NASA
- **Estimated Minimum Diameter** - Estimated minumum diameter of the object in kilometers
- **Estimated Maximum Diameter** - Estimated maximum diameter of the object in kilometers
- **Relative Velocity** - Velocity relative to Earth in Kmph
- **Miss Distance** - Distance in kilometers by which the object missed Earth
- **Orbiting Body**\* - The planet this asteroid orbits
- **Sentry Object**\* - Whether this object is included in an automated collision monitoring system known as Sentry
- **Absolute Magnitude** - Intrinsic luminosity of the object
- **Hazardous** - Boolean feature stating whether this asteroid is potentailly harmful or not

Fields marked with a \* will not be included in training to prevent either overfitting & leakage, or because the data is irrelevant.

## Approach
I plan on following the standard ML data model for processing the data, which would include feature engineering, modeling, and assessment. Our target is the boolean evaluation of whether or not a NEO is hazardous or not. To accomplish this, I will use a test/train split that will select a portion of the data (~70%) for training, a portion for validation (~20%), and a portion for testing (10%). The fields marked with an asterisk above would be excluded from the dataset used for training so as not fall prey to overfitting the model.

## Financial Incentives
NASA has a $138 million annual planetary defense budget, with a recent ear-marking of $90 milllion for the NEO Surveyor project, which is a space-based asteroid hunting telescope (which will not launch until 2028). The total cost of that mission has now reached $1.2 billion since it was approved in 2019. Given that we know that an asteroid is capable of being an extinction-level event, this is a small price to pay for increased awareness of what is out there. If you assume a risk of a 1:250,000 chance of an asteroid hitting an earth in a given year, it is a highly unlikely event that this should happen, but one that carries a very high price if we find ourselves in this position. Let's set up a scenario for evaluating the costs and savings afforded by this model:

If we assume the following as true for the sake of this exercise:
- A human life is worth $2 million
- The city of Los Angeles, CA has roughly 3.9 million people
- An asteroid strike that takes out Los Angeles kills 75% of the population (~3 million)
- The cost of such a strike would be almost $6 trillion
- The cost of a DART is $330 million dollars

It is quite easy to grasp that the cost of a false positive that results in an extra launch of a $330 million dollar spacecraft pales in comparison to almost $6 trillion. In fact, we would have to have *17,727* false positives to match the cost of a strike that takes out Los Angeles. Obviously, this is all hypothetical, but coming up with costs for something like this is quite difficult. To come up with real figures, a significant amount of time would need to be spent gathering data about natural disaster recovery costs, any/all data about actual impact restorations, the costs of monitoring NEO objects for both resources (satellites, radar, software) as well as man-hours, the costs of a data science team to build, train, deploy, & monitor the model, etc etc.

## Contact Information
Peter Thomas Keens: [Email](mailto:peter.t.keens@vanderbilt.edu)