# restaurant-outdoor-seating

Restaurant Operations Simulation (Discrete-Event System Analysis)

Overview
Developed a discrete-event simulation model in AnyLogic using Java-based agent logic to analyze the operational impact of expanding a restaurant from indoor-only seating to indoor and outdoor dining.
The project evaluates how increased customer demand affects system performance and identifies optimal resource allocation strategies to maintain service quality while maximizing profitability.
The simulation models end-to-end restaurant operations, including:
Customer arrivals (indoor and outdoor demand scenarios)
Multi-course meal processes (starter, main, dessert combinations)
Kitchen preparation and chef utilization
Waiter assignment and serving logic
Plate constraints and reuse cycles
Dishwashing capacity and bottlenecks

Objective
The main objective of the simulation was to evaluate whether the restaurant can maintain service quality after expanding seating capacity.
Service-Level Constraint:
No more than 10–12% of customers should wait longer than 30 minutes between ordering and recieving. 
Business Goal:
Determine the most cost-effective combination of:
staffing (waiters, chefs)
equipment (dishwasher, plates)
operational capacity
while maximizing profit under increased demand.

Model Design
The system is implemented as a discrete-event agent-based simulation in AnyLogic, structured around three main subsystems:
1. Customer Arrival System
Customers arrive based on time-dependent schedules for indoor and outdoor seating. Each customer is assigned a probabilistic meal structure (1–3 courses).
Course combinations are defined using empirical probabilities derived from observed restaurant behavior.
2. Service Loop (Core Restaurant Operation)
This loop simulates:
Order taking (waiter interaction)
Meal preparation (chef resource pool)
Serving process (waiter + plate constraints)
Eating time
Return of dirty dishes
Customers cycle through this loop until all ordered courses are completed.
Resource constraints include:
Chef availability
Waiter availability
Plate type (small vs large)
Service time distributions
3. Dishwashing System
Dirty plates enter a separate subsystem where a dishwasher processes them with:
Capacity constraint (number of plates per cycle)
Fixed cleaning time per batch
This subsystem acts as a secondary bottleneck affecting overall throughput.

Implementation Details
The model is built using Java logic inside AnyLogic, including:
Agent-based modeling (Customer, Chef, Waiter, Plate, Dishwasher)
Event-driven state transitions
Resource pools for staff and equipment
Custom Java functions for:
course assignment
delay time calculation
state management (remaining courses, exit condition)
A key function assigns customer orders probabilistically based on observed distributions and initializes each customer’s service path.

Experimental Design
Multiple scenarios were tested by varying:
Seating configuration (indoor only vs indoor + outdoor)
Number of chefs
Number of waiters
Plate inventory
Dishwasher capacity and speed
Each scenario was evaluated using:
Service-level compliance (waiting time threshold)
Total profit
System stability under high demand

Key Results
Baseline Scenario (Indoor Only)
Service level: ~2.70% SLA violations
Profit: ~€214,351

Outdoor Expansion (No changes)
Service level: ~58.26% SLA violations
Profit: ~€20,043
→ Significant degradation in performance due to overload

Equipment and Staffing Scenarios
Testing showed that:
Increasing plates alone does not solve system congestion
Upgrading dishwasher improves throughput but is not sufficient
Adding waiters improves service flow but does not remove core bottleneck
Increasing chef capacity has the strongest impact on system stability

Optimal Configuration
The best-performing configuration achieved:
~3.18% SLA violations (customers waiting > 30 minutes)
~€230,937 profit
Includes:
upgraded dishwasher
increased plate capacity
additional waiter(s)
optimized chef allocation (critical factor)
This configuration successfully balances:
service quality
operational throughput
profitability

Key Insight
The simulation identifies chef capacity as the primary system bottleneck.
Even when improving:
dishwashing speed
plate availability
waiter staffing
the system remains constrained unless chef capacity is increased.
This demonstrates that performance is not linearly improved by adding resources; instead, it is governed by bottleneck-driven throughput dynamics.

Conclusion
The analysis shows that expanding the restaurant without adjusting internal capacity leads to severe service degradation.
However, a carefully optimized resource configuration enables:
compliance with service-level targets
high system throughput
maximized profitability under increased demand

Recommendation:
To support outdoor seating expansion, the restaurant should:
upgrade dishwasher capacity and speed
increase plate availability
add at least one additional waiter
prioritize increasing chef capacity as the key operational improvement

Technologies Used
AnyLogic (Discrete-Event Simulation, Java-based modeling)
Java (agent logic and event programming)
Queueing Theory (system analysis)
Scenario-based optimization
