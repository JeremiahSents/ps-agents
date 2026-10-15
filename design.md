![Team diagram](docs/images/team.png)

## **1\. Introduction**

A self-driving trailer agent is an intelligent autonomous system designed to transport goods from one location to another without requiring continuous human control. It uses sensors to observe its surroundings, makes driving decisions using artificial intelligence, and performs actions through actuators.

## **2\. PEAS Framework**

| Component | Description |
| ----- | ----- |
| Performance Measure (P) | Ensure road safety, deliver cargo on time, minimize fuel consumption, obey traffic regulations, protect cargo, and reduce transportation costs. |
| Environment (E) | Highways, urban roads, other vehicles, pedestrians, traffic lights, road signs, weather conditions, loading stations, and delivery destinations. |
| Actuators (A) | Steering system, accelerator, braking system, indicators, headlights, horn, and trailer coupling controls. |
| Sensors (S) | Cameras, GPS, radar, LiDAR, ultrasonic sensors, speed sensors, weight sensors, and trailer articulation-angle sensors. |

## 3\. Classification of the Agent's Environment

The self-driving trailer operates in an environment characterized by five properties.

**1\. Partially Observable**

The trailer cannot observe everything around it. Blind spots, bad weather, obstacles, and sensor limitations may prevent it from obtaining complete information about its surroundings.

**2\. Stochastic**

The environment is unpredictable because other drivers, pedestrians, and weather conditions can change unexpectedly. The agent cannot always predict the outcome of its actions.

**3\. Sequential**

Each driving decision affects future decisions. For example, changing lanes influences the trailer's position and the actions required to reach its destination safely.

**4\. Dynamic**

The environment changes continuously while the agent is making decisions. Vehicles move, traffic lights change, and pedestrians cross roads.

**5\. Multi-Agent**

The trailer operates alongside other decision-making agents, including human drivers, pedestrians, cyclists, and autonomous vehicles.

## **4\. How the Agent Operates**

The self-driving trailer follows a continuous decision-making process:

1. Perception: Sensors collect information about road conditions, surrounding vehicles, obstacles, and trailer movement.  
2. Processing: The AI system analyzes the collected information and identifies potential risks.  
3. Decision-making: The agent determines appropriate actions such as accelerating, braking, turning, or changing lanes.  
4. Action: Actuators execute the selected decisions.  
5. Monitoring: The agent continuously observes the results and adjusts its actions to maintain safety.

For example, when the trailer detects a vehicle braking ahead, its sensors provide the information to the AI system, which calculates a safe stopping distance and activates the brakes.

## **5\. Conclusion**

The self-driving trailer is designed to transport goods safely, efficiently, and autonomously. Using the PEAS framework helps identify its objectives, operating environment, actions, and sensing capabilities.

Its environment is partially observable, stochastic, sequential, dynamic, and multi-agent, requiring the agent to continuously monitor its surroundings and adapt its decisions.

## **Directed Graph**
```mermaid
graph LR
    subgraph Nairobi
        NBI[Nairobi]
    end
    subgraph Central_Highlands
        THK[Thika]
        NYR[Nyeri]
        NYK[Nanyuki]
        NYH[Nyahururu]
    end
    subgraph Rift_Valley
        NVS[Naivasha]
        NKR[Nakuru]
        NRK[Narok]
        KER[Kericho]
        ELD[Eldoret]
    end
    subgraph Lake_Victoria_Basin
        KSM[Kisumu]
        KSI[Kisii]
        KAK[Kakamega]
        WEB[Webuye]
    end

    NBI -->|45| THK
    NBI -->|90| NVS
    NBI -->|142| NRK
    THK -->|105| NYR
    NYR -->|60| NYK
    NYR -->|100| NYH
    NYH -->|70| NKR
    NVS -->|70| NKR
    NKR -->|107| KER
    NKR -->|156| ELD
    NRK -->|170| KSI
    KER -->|84| KSM
    KER -->|100| KSI
    ELD -->|115| KAK
    ELD -->|60| WEB
    WEB -->|40| KAK
    KAK -->|52| KSM
    KSI -->|112| KSM
```

## **Full Tree**
```mermaid
graph TD
    F1["Nairobi<br/>g = 0"]
    F2["Thika<br/>g = 45"]
    F1 -->|45| F2
    F3["Nyeri<br/>g = 150"]
    F2 -->|105| F3
    F4["Nanyuki<br/>g = 210"]
    F3 -->|60| F4
    F5["Nyahururu<br/>g = 250"]
    F3 -->|100| F5
    F6["Nakuru<br/>g = 320"]
    F5 -->|70| F6
    F7["Kericho<br/>g = 427"]
    F6 -->|107| F7
    F8["Kisumu<br/>g = 511"]
    F7 -->|84| F8
    F9["Kisii<br/>g = 527"]
    F7 -->|100| F9
    F10["Kisumu<br/>g = 639"]
    F9 -->|112| F10
    F11["Eldoret<br/>g = 476"]
    F6 -->|156| F11
    F12["Webuye<br/>g = 536"]
    F11 -->|60| F12
    F13["Kakamega<br/>g = 576"]
    F12 -->|40| F13
    F14["Kisumu<br/>g = 628"]
    F13 -->|52| F14
    F15["Kakamega<br/>g = 591"]
    F11 -->|115| F15
    F16["Kisumu<br/>g = 643"]
    F15 -->|52| F16
    F17["Naivasha<br/>g = 90"]
    F1 -->|90| F17
    F18["Nakuru<br/>g = 160"]
    F17 -->|70| F18
    F19["Kericho<br/>g = 267"]
    F18 -->|107| F19
    F20["Kisumu<br/>g = 351"]
    F19 -->|84| F20
    F21["Kisii<br/>g = 367"]
    F19 -->|100| F21
    F22["Kisumu<br/>g = 479"]
    F21 -->|112| F22
    F23["Eldoret<br/>g = 316"]
    F18 -->|156| F23
    F24["Webuye<br/>g = 376"]
    F23 -->|60| F24
    F25["Kakamega<br/>g = 416"]
    F24 -->|40| F25
    F26["Kisumu<br/>g = 468"]
    F25 -->|52| F26
    F27["Kakamega<br/>g = 431"]
    F23 -->|115| F27
    F28["Kisumu<br/>g = 483"]
    F27 -->|52| F28
    F29["Narok<br/>g = 142"]
    F1 -->|142| F29
    F30["Kisii<br/>g = 312"]
    F29 -->|170| F30
    F31["Kisumu<br/>g = 424"]
    F30 -->|112| F31
    classDef goal fill:#b6d7a8,stroke:#38761d,stroke-width:2px
    class F8,F10,F14,F16,F20,F22,F26,F28,F31 goal
```
## **Abstracted Tree**
```mermaid
graph TD
    A["Nairobi<br/>g = 0 · #1"]
    B["Thika<br/>g = 45 · #2"]
    C["Naivasha<br/>g = 90 · #3"]
    D["Narok<br/>g = 142 · #4"]
    E["Nyeri<br/>g = 150 · #5"]
    F["Nakuru<br/>g = 160 · #6"]
    G["Nanyuki<br/>g = 210 · #7<br/>dead end"]
    H["Nyahururu<br/>g = 250 · #8"]
    I["Nakuru<br/>g = 320<br/>pruned: explored at 160"]
    J["Kericho<br/>g = 267 · #9"]
    K["Kisii<br/>g = 312 · #10"]
    L["Eldoret<br/>g = 316 · #11"]
    M["Kisumu<br/>g = 351 · #12<br/>GOAL"]
    N["Kisii<br/>g = 367<br/>pruned: in frontier at 312"]
    O["Kisumu<br/>g = 424<br/>pruned: in frontier at 351"]
    P["Webuye<br/>g = 376<br/>not expanded"]
    Q["Kakamega<br/>g = 431<br/>not expanded"]
    A -->|45| B
    A ==>|90| C
    A -->|142| D
    B -->|105| E
    E -->|60| G
    E -->|100| H
    H -->|70| I
    C ==>|70| F
    F ==>|107| J
    F -->|156| L
    J ==>|84| M
    J -->|100| N
    D -->|170| K
    K -->|112| O
    L -->|60| P
    L -->|115| Q
    classDef goal fill:#b6d7a8,stroke:#38761d,stroke-width:3px
    classDef pruned fill:#f4cccc,stroke:#990000,stroke-dasharray:5 5
    classDef frontier fill:#fff2cc,stroke:#bf9000
    classDef dead fill:#eeeeee,stroke:#666666
    class M goal
    class I,N,O pruned
    class P,Q frontier
    class G dead
```



