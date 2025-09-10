# knowledge-and-agent-systems

##Rapport

1. walktrough of the four legal cases
 1.1 Jacob
  1.1.1 Description
   Jacob is an intellectually disabled man of the age of 30. While playing,       and without
     realising that he does something wrong, he destroys the rose bushes in         the garden of his
     neighbor Henk. Does Jacob have to repair the damages done to Henk based        on a tortious act

1.1.2 Walktrough
1. Was there a violation of someone´s right OR anc act/omission against a legal duty or proper social conduct?
   answer: yes
   why: Destroying Henk´s property violates his property rights (Art. 6:162)


2. Was there a justification (e.g., emergency rescue/necessity)?
   answer: no
   why: playing isnt a legal justification
   
3. How old is the person
   answer: 14 years or older
   why: the person is 30 years old
   
4. was the act done under a mental or physical disability?
   answer: yes
   why: Jacob is a intellecttually disabled man

5. Did the violated standard intend to protect against this type of damage?
   answer: yes
   why: Property rules protect against damage to property

1.1.3 conclusions
Is the person liable for damages?
  yes: must repair damage
                          
                           
1.2 Maria
     1.2.1 description
      Maria is deaf. Johannes, age 11, has fallen into the water and screams         for help. Maria
      does not notice and therefore does not save Johannes. Johannes drowns.         Does Maria have
      to repair the damages done to Johannes’ next of kin based on a tortious        act?

1.2.2 walktrough
1. Was there a violation of someone´s right OR anc act/omission against a legal duty or proper social conduct?
   answer: No
   why: No legal duty to hear/sense calls for help. the omission isn´t            unlawful under 6:162(2)
1.2.3 conclusion
Not liable, without unlawfulness, there is no tortious act (6:162), so no duty to repair
    

   1.3 Berend
   1.3.1 Description
   Berend notices that the house of old Ank is on fire. To save her, he breaks    a window of
   the house. He is able to get Ank out of the house in time. Ank suffers        damage because she
  has to replace the broken window. Does Berend have to repair the damages       done to Ank
  based on a tortious act?

1.3.2 Walktrough
1. Was there a violation of someone´s right OR anc act/omission against a legal duty or proper social conduct?
   answer: yes
   why:breaking a window violates property rights
2. Was there a justification (e.g., emergency rescue/necessity)?
   answer: yes
   why: Emergency rescue is a classic justification/necessity defense

1.3.3 conclusion
result: not liable
why: there was a rights violation, but this violation was justified (6:162(2)), so no tortious act and no liablity
   
1.4 Henk
1.4.1 description
 Henk violates the legislation regarding shopping hours by opening his furniture shop on
Sundays. The municipality condones Henk’s practices. Leo, who owns a furniture shop
in the neighbouring municipality, is not allowed to open his shop on Sundays. Leo suffers
damages due to the loss of customers. Does Henk have to repair the damages done to Leo
based on a tortious act?

1.4.2 walktrough
1. Was there a violation of someone´s right OR anc act/omission against a legal duty or proper social conduct?
   answer: yes
   why: Henk violates shop hour legislation
2. Was there a justification (e.g., emergency rescue/necessity)?
   answer: no
   why: No justification was given. condoning dosent make it a legal           justification

3.Can the act be attributed to the person (fault or cause for which they are accountable)?
  answer: yes
  why: Henk opened the store intentionally

4. Did the violated standard intend to protect against this type of damage?
   answer: no
   why: Shop-hour rules arent meant to protect against a competitors revenue (Art. 6:163)

1.4.3 conclusion
is the person liable for damages?
no: no obligation to repair
--> the liability is blocked by 6:163 because the violated rule doesn´t aim to protect againt leo´s type of loss
  
  
   
7. Description of the design of the knowledge system

   3.1 Goal and scope
The system gives out advice if a person should repair damages based on a tortious/unlawful act under the dutch civil code articles \textbf${6:162-6:165$}, limited by \textbf${6:163}$.
The design is keeping the questioning minimal and all the explenations traceable
   3.2 representation
For the design I used the XML format with:
- facts (discrete values)
- Questions (to elict facts)
- Rules (if/then derivation) and a single goal liable with answers yes/no/insufficient

The engine uses something called backward chaining. It starts from the goal, asks the most informative questions, incorporates the answers as a fact, and re-runs inference until liable is decided

   3.3 Modeling choices
6:162 bundles several conditions, where these where split into explicit facts so that each element can be visible and testable

unlawfulness gives us the choice between unlawful =yes/no. This covers "violation of someones right" and "act/omission against a legal duty or proper social conduct

Justification gives us a anser if there was a justification for the act or not

3.4 attributions
The capacity affects only the attribution and not unlawfulness. I encoded the two statutory exceptions as rules that override any answer to the attribution question:
6:164 (child < 14): age=under14 ==> attributable=no
6:165 (>14 with disability): age=14_or_older ∧ disability=yes ==> attributable=yes

3.5 Decision rules
Liability requires all three:
tortious_act = yes ∧ attributable = yes ∧ protected_standard = yes ==> liable = yes

i also added so called gatekeepers so that any missing elements denies liability

Tortious_act=no ==> liable=no; attributable=no ==> liable=no; protected_standard=no ==> liable=no
 by implementing this the system becomes more cautious and reduces false positivness

3.6 vocabulary
There are small value sets used here, such as
Binary: yes/no for unlawful, disability, justified, protected_standard and attributable


3.7 Assumptions and limitations
The test is abstracted into one question (rights violation, legal duty and proper social conduct). If this was a bigger system I would have split these into seperate prompts and add causation/damage checks, but this was not in the scope of the assigment



