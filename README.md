```mermaid
graph TD
    classDef stateFill fill:#e1f5fe,stroke:#01579b,stroke-width:2px;
    classDef agentFill fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px;
    classDef toolFill fill:#fff3e0,stroke:#ef6c00,stroke-width:2px;
    
    START([User Profile Ingested]) --> |JSON Payload| State[(Central State Memory)]
    class State stateFill;

    State --> |physical_limitations| Node1[Node 1: Health & Injury Analyst]
    class Node1 agentFill;
    Node1 <--> NativeTavily[Native Tavily Tool]
    class NativeTavily toolFill;
    Node1 --> |injury_insights| State

    State --> |injury_insights & fatigue| Node2[Node 2: Adaptive Personal Trainer]
    class Node2 agentFill;
    Node2 <--> ExerciseDB[ExerciseDB API Tool]
    class ExerciseDB toolFill;
    Node2 --> |workout_plan| State

    State --> |workout_plan & history| Node3[Node 3: Nutritional Strategist]
    class Node3 agentFill;
    Node3 <--> USDA[USDA FoodData API Tool]
    class USDA toolFill;
    Node3 --> |nutrition_plan| State

    State --> |synthesized data| Node4[Node 4: Plan Coordinator]
    class Node4 agentFill;
    Node4 --> |Timeline layout| Output[Final Output: Daily Itinerary]
    Output --> END([Execution Complete])
