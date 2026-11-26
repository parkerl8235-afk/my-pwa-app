# Latoya Garden Planner v6.17.2 Runtime Repair

Root cause: V6.17 replaced the old Dashboard HTML but left the original synchronous Dashboard renderer in the script. It immediately queried removed IDs (`dashSearch`, `germTotal`, `seedTotal`, `plantTotal`, `attention`, and `dashCrops`) and threw a null-reference error. Because all later controllers are in the same script block, the error prevented both Dashboard and Garden Map click handlers from being registered.

This repair restores the expected legacy IDs in a hidden compatibility container while leaving the visible V6.17 Dashboard and stable V6.14 map implementation unchanged.
