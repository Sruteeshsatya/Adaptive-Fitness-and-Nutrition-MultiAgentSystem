# Personal Health & Fitness Multi-Agent System (MAS)

An intelligent, state-driven multi-agent framework built with **LangGraph** and **Gemini 2.5 Flash** that generates highly personalized, injury-aware, and fatigue-responsive training and nutritional plans.

## 🚀 System Architecture
Our architecture utilizes a centralized, state-managed flowchart pattern to ensure full collaboration between specialized agents while strictly isolating physical constraints:

```mermaid
graph TD
    START([User Profile Ingested]) --> State[(Central State Memory)]
    State --> Node1[Health & Injury Analyst]
    Node1 <--> NativeTavily[Native Tavily Tool]
    Node1 --> State
    State --> Node2[Adaptive Personal Trainer]
    Node2 <--> ExerciseDB[ExerciseDB API Tool]
    Node2 --> State
    State --> Node3[Nutritional Strategist]
    Node3 <--> USDA[USDA FoodData API Tool]
    Node3 --> State
    State --> Node4[Plan Coordinator / Orchestrator]
    Node4 --> Output[Final Customized Itinerary]
