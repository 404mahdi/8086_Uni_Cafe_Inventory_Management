# University Cafe Inventory Management System

**Course:** 341 - Fall 2025  
**Language:** 8086 Assembly Language  
**Platform:** DOS (MS-DOS/DOSBox)

## Project Overview

This is a command-line inventory management system written in 8086 assembly language for managing a university cafe's stock. The system provides real-time tracking of inventory items, pricing management, low-stock alerts, and asset valuation calculations.

## Features

### 1. **Password Authentication**

- Admin password protection (default: `1234`)
- Multiple login attempts allowed
- Secure access to inventory management functions

### 2. **Stock Dashboard**

- Display all inventory items with current stock levels
- Shows item ID, name, quantity, and price
- Real-time inventory status

### 3. **Add Inventory**

- Add stock quantities to existing items
- Input validation for item IDs (1-5)
- Immediate stock level updates

### 4. **Update Price**

- Modify individual item prices
- Dynamic pricing capability
- Instant price updates across the system

### 5. **Low Stock Audit**

- Automatic detection of items below minimum threshold
- Configurable minimum stock level (default: 5 units)
- Warning alerts for restocking needs

### 6. **Total Asset Valuation**

- Calculate total inventory value
- Formula: Sum of (Price × Stock) for all items
- Financial overview of current assets

## Inventory Items

| ID  | Item Name | Initial Stock | Initial Price |
| --- | --------- | ------------- | ------------- |
| 1   | Coffee    | 10            | 20            |
| 2   | Tea       | 8             | 10            |
| 3   | Sandwich  | 4             | 60            |
| 4   | Muffin    | 6             | 15            |
| 5   | Juice     | 3             | 50            |

## Technical Specifications

### Memory Model

- **Model:** Small
- **Stack Size:** 100H (256 bytes)

### Data Structures

- **ProductPtrs:** Array of pointers to item name strings
- **StockArray:** Array of word values for quantities
- **PriceArray:** Array of word values for prices

### Key Procedures

- `PrintDashboard` - Display current inventory status
- `AddInventory` - Add quantity to stock
- `UpdatePrice` - Update item price
- `LowStockAudit` - Check and report low stock items
- `TotalValuation` - Calculate total inventory value
- `ReadNumber` - Parse decimal input from user
- `PrintNum` - Display decimal numbers

## System Requirements

- **Assembler:** MASM (Microsoft Macro Assembler) or compatible
- **Emulator:** DOSBox or similar DOS environment
- **Memory:** Minimal (< 1KB data segment)

## How to Compile and Run

### Using MASM

```bash
# Assemble the source code
masm main.asm;

# Link the object file
link main.obj;

# Run the executable
main.exe
```

### Using DOSBox

```bash
# Mount the project directory
mount d: d:\Projects\8086-uni-cafe-inventory-management

# Change to the mounted drive
d:

# Assemble
masm main.asm;

# Link
link main.obj;

# Run
main.exe
```

## Usage Instructions

1. **Launch the program**

   - Enter admin password: `1234`

2. **Main Menu Options**

   ```
   1. Stock Dashboard      - View all items and stock levels
   2. Add Inventory        - Increase stock quantity
   3. Update Price         - Change item price
   4. Low Stock Audit      - Check items needing restock
   5. Total Asset Valuation - Calculate total inventory value
   6. Exit                 - Close the program
   ```

3. **Adding Inventory**

   - Select option 2
   - Enter item ID (1-5)
   - Enter quantity to add
   - Stock will be updated immediately

4. **Updating Prices**

   - Select option 3
   - Enter item ID (1-5)
   - Enter new price
   - Price will be updated immediately

5. **Low Stock Audit**

   - Select option 4
   - System displays items with stock below threshold (5 units)

6. **Total Valuation**
   - Select option 5
   - System calculates and displays total inventory value

## Program Flow

```
┌─────────────────────┐
│  Password Login     │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│   Main Menu Loop    │
└──────────┬──────────┘
           │
     ┌─────┴─────┬─────────┬──────────┬──────────┬─────────┐
     ▼           ▼         ▼          ▼          ▼         ▼
  Dashboard    Add    Update      Audit      Valuation   Exit
  Display    Stock    Price     Low Stock     Total
```

## Customization

### Changing Password

Modify the `PASSWORD` variable in the data segment:

```assembly
PASSWORD        DB '1234'  ; Change to your desired password
PASSWORD_LEN    DB 4        ; Update length accordingly
```

### Adjusting Minimum Stock Level

Modify the `MIN_STOCK` variable:

```assembly
MIN_STOCK       DW 5  ; Change to desired threshold
```

### Adding More Items

1. Add item name string in data segment
2. Add pointer to `ProductPtrs` array
3. Add initial values to `StockArray` and `PriceArray`
4. Update loop counters (currently set to 5)

## Learning Objectives Demonstrated

- ✅ Memory segmentation and addressing modes
- ✅ Array manipulation with word-sized data
- ✅ String operations and pointer arithmetic
- ✅ Arithmetic operations (multiplication for valuation)
- ✅ Conditional branching and loop structures
- ✅ DOS interrupts (INT 21H) for I/O operations
- ✅ Procedure design and modular programming
- ✅ Stack operations and register management
- ✅ Number parsing and formatting algorithms

## Project Structure

```
8086-uni-cafe-inventory-management/
├── main.asm          # Main source code
└── README.md         # This file
```

## Known Limitations

- Maximum 5 items (can be extended with code modifications)
- Single-user system (no concurrent access)
- No persistent storage (data resets on exit)
- Input validation is basic (assumes correct numeric input)
- Maximum input value limited by 16-bit word size (0-65535)

## Future Enhancements

- [ ] Add file-based persistence for inventory data
- [ ] Implement sales transaction recording
- [ ] Add item search functionality
- [ ] Support for decimal/fractional pricing
- [ ] Generate inventory reports
- [ ] Multi-level user access (admin/staff)

## Author Notes

This project demonstrates fundamental assembly language programming concepts including memory management, I/O operations, and algorithmic implementation at the hardware level. The system provides practical experience with low-level programming while solving a real-world business problem.

## License

Academic project for educational purposes - Course 341, Fall 2025

---

_For questions or issues, please consult course materials or contact the instructor._
