# SAP Test Harness MVP 0.15

## Overview
A test harness that simulates SAP API behavior for P2P (Procure-to-Pay) operations, focusing on material management and procurement processes. Built for MVP 0.1, it provides basic functionality for testing without requiring an actual SAP system.

## Features
- Material management simulation
- P2P process flow testing
- Document state tracking
- Error case validation
- Multi-document relationship testing

## Directory Structure
```
test_harness/
  mock_sap/
    __init__.py
    sap_types.py         # Core type definitions
    api_operations.py    # Material management
    api_simulator.py     # Core simulator engine
    p2p_apis.py         # P2P operations
  tests/
    __init__.py
    test_config.py      # Test configuration
    test_material_ops.py # Material tests
    test_p2p_flow.py    # P2P flow tests
    test_runner.py      # Test execution
```

## Core Components

### Type System (sap_types.py)
- Standard response and error types
- Consistent API behavior
- Type validation
- Error handling

### Material Management (api_operations.py)
- Material availability checks
- Stock level management
- Material master data
- Basic validation

### API Simulator (api_simulator.py)
- Core simulation engine
- Authentication handling
- Request routing
- State management

### P2P Operations (p2p_apis.py)
- Purchase Requisition handling
- Purchase Order management
- Document flow tracking
- State management

## Test Framework

### Test Runner (test_runner.py)
- Unified test execution
- State management
- Result aggregation
- Performance tracking

### Test Categories
1. Material Operations Tests
   - Material availability
   - Material creation
   - Stock management

2. P2P Flow Tests
   - Document creation
   - State transitions
   - Validation rules

3. Error Case Tests
   - Invalid inputs
   - State violations
   - Authentication failures

4. Multi-Document Tests
   - Document relationships
   - State consistency
   - Flow validation

## Quick Start

### Requirements
```
pytest==7.4.3
pytest-asyncio==0.21.1
pytest-cov==4.1.0
typing-extensions>=4.8.0
python-dateutil>=2.8.2
```

### Basic Usage
```python
# Initialize components
material_mgmt = MockMaterialManagement()
p2p_simulator = P2PSimulator(material_management=material_mgmt)

# Run material check
response = await material_mgmt.check_material_availability(
    material_id='MAT001',
    plant='PLANT_1'
)

# Create PR
pr_response = await p2p_simulator.create_purchase_requisition({
    'material_id': 'MAT001',
    'quantity': 100,
    'delivery_date': '2024-03-01',
    'plant': 'PLANT_1'
})
```

### Running Tests
```bash
# Run all tests
python -m pytest test_harness/tests -v

# Run specific test category
python -m pytest test_harness/tests/test_material_ops.py -v
```

## Google Colab Support
The test harness includes a Google Colab scaffolding for easy execution and testing. See `SAP_test_harness_v0_1_simple_v4.ipynb` for details.

## State Management
- Maintains consistent state across operations
- Tracks document relationships
- Provides state snapshots
- Supports state reset

## Error Handling
- Standard error responses
- Detailed error messages
- State capture on failure
- Validation checks

## Limitations
- MVP 0.1 version with basic functionality
- Limited to core P2P operations
- Basic authentication simulation
- Single plant support

## Future Enhancements
- Additional SAP modules
- Extended P2P functionality
- Multi-plant support
- Advanced authentication
- Performance optimizations

## Contributing
1. Fork the repository
2. Create a feature branch
3. Make changes
4. Run test suite
5. Submit pull request

## License
MIT License

## Contact
For issues and suggestions, please create a GitHub issue.