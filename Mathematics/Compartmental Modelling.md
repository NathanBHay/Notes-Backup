Compartmental modelling is an approach of [[Modelling|modelling]] through the use of multiple states or sets in which actors of a population transition. The key parts of a compartmental model is that there exists a population that can be subdivided into compartments. Each of these compartments representing a state that a member of the population travels through. With the acronym for the model usually representing the order in which an individual is classified within the groups. Compartmental modelling is mostly used within the epidemiology field to model the spread of infectious diseases. There are a variety of approaches to modelling disease spread however all stem from the main SIR model.

# SIR Model
The SIR model is a simple compartmental model that splits the population into three main groups based on the disease. Those groups are:
- **Susceptible** class $S(t)$ represents the population within the system who are yet to be infected.
- **Infected** class $I(t)$ contains those with the disease who are able to infect those within the susceptible group.
- **Recovered** class $R(t)$ is the people who are no longer considered infected and have built up an immunity to being infected again.

These groups function along a time unit $t$, where $S(t)+I(t)+R(t)=N$, where $N$ is the total population within the model.

The SIR model is most effective at modelling diseases which have a permanent recovery and a quick rate of infection.

## SIRS
The SIRS model is an expansion upon the SIR model that in addition to the previous traits also has a transition from recovered to susceptible again. This change to the model is important for viruses that only have temporary immunity.

## SEIRS
The SEIRS model further expands upon the SIR and SIRS model by adding an **exposed** category, which represents the time it takes for a virus to reach an infected status.