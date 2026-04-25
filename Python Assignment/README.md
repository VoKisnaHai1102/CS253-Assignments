# Python Assignment

## Files

```
Python Assignment/
├── Question_1.py    # ASCII invitation card generator
├── Question_2.py    # Recursive crafting simulator
├── Question_3.py    # Campus navigation (Dijkstra)
├── Question_4.py    # 2D image convolution from scratch
├── Question_5.py    # Railway freight routing simulator
├── Python Assignment Question.pdf
└── README.md
```

## Requirements

Python 3.8+ with NumPy (only needed for `Question_4.py`):

```bash
pip install numpy
```

No other third-party dependencies.

## Running Each File

Each file is standalone and can be run directly. Each contains the solution function and a block with a sample test case.

```bash
python Question_1.py
python Question_2.py
python Question_3.py
python Question_4.py
python Question_5.py
```

## Function Reference

| File | Function | Signature |
|------|----------|-----------|
| `Question_1.py` | Invitation generator | `generate_invites(guest_list, event_details) → dict` |
| `Question_2.py` | Raw materials calculator | `calculate_raw_materials(item, quantity, recipes) → dict` |
| `Question_3.py` | Shortest campus route | `find_safe_route(graph, start, end, blocked_nodes) → tuple` |
| `Question_4.py` | Image convolution | `apply_filter(image, kernel) → np.ndarray` |
| `Question_5.py` | Delivery simulation | `run_delivery_schedule(train, network, route_list) → float` |

### Importing into your own code

```python
from Question_1 import generate_invites
from Question_2 import calculate_raw_materials
from Question_3 import find_safe_route
from Question_4 import apply_filter
from Question_5 import (
    PhysicsConstraintError, RollingStock, Locomotive,
    FreightCar, Train, RailwayNetwork, run_delivery_schedule
)
```
