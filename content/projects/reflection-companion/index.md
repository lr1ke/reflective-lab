**Reflection Companion: Interactive Journaling with AI**

Conversational agents are making human-computer interaction increasingly collaborative and conversational through the use of natural language. **Reflection Companion** is a proof of concept exploring the design of conversational interactions for reflection and journaling. It investigates interactive and reflective journaling with conversational agents and the experience of writing self-reflection with AI Chatbots.

The project is situated in the area of personal informatics, with the goal of designing conversational agents that support reflective thinking and help users improve their self-knowledge through self-reflection. It approaches journaling not only as a way of recording experiences and thoughts, but as a process in which these experiences can be revisited, questioned, and developed through dialogue.

As design principles for interactive and reflective journaling with AI, the proof of concept draws on established personal-development frameworks. These frameworks provide the material from which different conversational interactions are constructed.

Stephen Covey's *The 7 Habits of Highly Effective People* describes seven habits intended to spur and nurture personal change. The first three are concerned with what Covey describes as independence. Two of these habits form the basis of two conversational agents. 

One companion is based on the first habit, *Be Proactive*. It concerns taking responsibility for one's response to one's own experiences and recognizing the possibility of choosing how to react to a situation. Covey's account draws on the work of psychiatrist Viktor Frankl and the idea that between stimulus and response lies a person's ability to choose their response. The conversation translates this principle into a framework for reflecting on an experience, one's reaction to it, and possible ways of responding differently.

The second agent focuses on envisioning what one wants in the future in order to work and plan toward it. The conversation uses this future perspective to reflect on present decisions, priorities, and direction. It’s based on the second habit: *Begin with the End in Mind*.

A further conversational interaction draws on *The ONE Thing* by Gary Keller and Jay Papasan. The book develops an approach to prioritization around the focusing question: What’s the one thing I can do such that by doing it everything else will be easier or unnecessary? The Chatbot translates this principle of prioritizing a single task into everyday decision-making and provides a structure for reflecting on competing priorities and possible next actions.

Reflection Companion is designed as a support tool for reflection on experiences, thoughts, and evolving insights. The different conversations provide initial frameworks through which users can analyze resistance patterns, develop new perspectives, and reflect on possible changes in their behavior.

The underlying assumption is that reflection as a learning process requires several skills, including self-awareness, description, critical analysis, synthesis, and evaluation. Improving self-knowledge similarly requires a more knowing and critical view of past experiences, with the purpose of clarifying feelings, personal values, beliefs, and traits. Interactive journaling with a conversational agent provides one possible setting in which these processes can be explored through writing and dialogue.

Future work will focus more closely on these learning aspects of reflection. On the one hand, the project aims to investigate whether personal informatics systems and conversational tools can support the development of reflective skills and whether repeated reflective interaction can contribute to improved self-knowledge over time.

On the other hand, let’s assume reflection is also a collective process, a collaborative experience that is best represented computationally as an abstraction layer on top of individual reflections. The hypothesis is that the individual may need the collective in order to reflect on itself.

Reflection Companion already experiments with this idea through a collective diary. After each reflective conversation, an AI agent acting as a scribe synthesizes the insights of the chat into an anonymous diary entry, which becomes part of a shared thread. A next step will explore a **collective reflection layer on top of these individual diary entries**, potentially facilitated through GraphRAG technology. A first experiment with this approach was developed for [Collective Diary](https://github.com/lr1ke/neo4j-hack), using Neo4j to model relationships and patterns across individual agent histories.