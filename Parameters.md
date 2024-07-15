# Parameters

### 1. **CPU - RAM Compatibility**

**Parameters:**
- **CPU RAM Type**: The type of RAM supported by the CPU (e.g., DDR4, DDR5).
- **CPU Max RAM Speed**: The maximum RAM speed supported by the CPU (e.g., 3200 MHz).
- **RAM Type**: The type of the RAM module (e.g., DDR4, DDR5).
- **RAM Speed**: The speed of the RAM module (e.g., 3200 MHz).

**Logic:**
- Check if `CPU RAM Type` matches `RAM Type`.
- Check if `RAM Speed` is less than or equal to `CPU Max RAM Speed`.

### 2. **CPU - Motherboard Compatibility**

**Parameters:**
- **CPU Socket Type**: The socket type of the CPU (e.g., LGA1200, AM4).
- **CPU Supported Chipsets**: The chipsets supported by the CPU (e.g., Z590, B550).
- **Motherboard Socket Type**: The socket type of the motherboard (e.g., LGA1200, AM4).
- **Motherboard Chipset**: The chipset of the motherboard (e.g., Z590, B550).

**Logic:**
- Check if `CPU Socket Type` matches `Motherboard Socket Type`.
- Check if `Motherboard Chipset` is in `CPU Supported Chipsets`.

### 3. **CPU - SSD Compatibility**

**Parameters:**
- **Motherboard**: Used as a bridge parameter since CPU does not directly interface with SSD.
- **CPU Socket Type**: The socket type of the CPU.
- **Motherboard Socket Type**: The socket type of the motherboard.
- **Motherboard Supported Storage Interfaces**: Storage interfaces supported by the motherboard (e.g., SATA, NVMe).

**Logic:**
- Ensure `CPU Socket Type` matches `Motherboard Socket Type` (from the CPU-Motherboard compatibility check).
- Ensure `Motherboard Supported Storage Interfaces` include the interface of the SSD.

### 4. **RAM - Motherboard Compatibility**

**Parameters:**
- **RAM Type**: The type of the RAM module (e.g., DDR4, DDR5).
- **RAM Speed**: The speed of the RAM module (e.g., 3200 MHz).
- **Motherboard RAM Type**: The type of RAM supported by the motherboard (e.g., DDR4, DDR5).
- **Motherboard Max RAM Speed**: The maximum RAM speed supported by the motherboard (e.g., 3200 MHz).

**Logic:**
- Check if `RAM Type` matches `Motherboard RAM Type`.
- Check if `RAM Speed` is less than or equal to `Motherboard Max RAM Speed`.

### 5. **RAM - SSD Compatibility**

**Parameters:**
- **RAM**: Used as a bridge parameter since RAM does not directly interface with SSD.
- **Motherboard Supported Storage Interfaces**: Storage interfaces supported by the motherboard (e.g., SATA, NVMe).

**Logic:**
- Ensure `Motherboard Supported Storage Interfaces` include the interface of the SSD.

### 6. **SSD - Motherboard Compatibility**

**Parameters:**
- **SSD Interface**: The interface of the SSD (e.g., SATA, NVMe).
- **SSD Form Factor**: The form factor of the SSD (e.g., 2.5-inch, M.2).
- **Motherboard Supported Storage Interfaces**: Storage interfaces supported by the motherboard (e.g., SATA, NVMe).
- **Motherboard Supported Form Factors**: Form factors supported by the motherboard (e.g., 2.5-inch, M.2).

**Logic:**
- Check if `SSD Interface` is in `Motherboard Supported Storage Interfaces`.
- Check if `SSD Form Factor` is in `Motherboard Supported Form Factors`.

### Integrating the Compatibility Checker with the Chatbot

When a user asks about compatibility, the chatbot can collect the necessary specifications and use the `CompatibilityChecker` to validate the combinations:

1. **Collect Specifications**: Gather details about the CPU, motherboard, RAM, and SSD from the user.
2. **Check Compatibility**: Use methods from `CompatibilityChecker` to validate each combination.
3. **Provide Feedback**: Inform the user about compatibility and suggest alternatives if needed.

This structure ensures your chatbot can provide accurate and helpful recommendations for PC builds.


To ensure the compatibility checker works effectively, you'll need to structure your data in Excel with columns that capture the key parameters for each component type. Here's a suggested structure for each component:

### CPU Excel File

**Columns:**
- **Model**: The model name of the CPU (e.g., Intel Core i9-11900K).
- **Socket Type**: The socket type (e.g., LGA1200, AM4).
- **Supported Chipsets**: The chipsets supported by the CPU (e.g., Z590, B560, H570).
- **Max RAM Speed**: The maximum RAM speed supported (e.g., 3200 MHz).
- **Memory Type**: The type of RAM supported (e.g., DDR4, DDR5).

### Example:

| Model               | Socket Type | Supported Chipsets        | Max RAM Speed | Memory Type |
|---------------------|-------------|---------------------------|---------------|-------------|
| Intel Core i9-11900K| LGA1200     | Z590, B560, H570          | 3200          | DDR4        |
| AMD Ryzen 9 5900X   | AM4         | X570, B550                | 3200          | DDR4        |

### RAM Excel File

**Columns:**
- **Model**: The model name of the RAM (e.g., Corsair Vengeance LPX 16GB).
- **Type**: The type of RAM (e.g., DDR4, DDR5).
- **Speed**: The speed of the RAM (e.g., 3200 MHz).

### Example:

| Model                     | Type  | Speed |
|---------------------------|-------|-------|
| Corsair Vengeance LPX 16GB| DDR4  | 3200  |
| G.Skill Trident Z RGB 32GB| DDR4  | 3600  |

### SSD Excel File

**Columns:**
- **Model**: The model name of the SSD (e.g., Samsung 970 EVO Plus 1TB).
- **Interface**: The interface type (e.g., SATA, NVMe).
- **Form Factor**: The form factor (e.g., 2.5-inch, M.2).
- **Protocol**: The protocol used (e.g., AHCI for SATA, NVMe for PCIe).

### Example:

| Model                   | Interface | Form Factor | Protocol |
|-------------------------|-----------|-------------|----------|
| Samsung 970 EVO Plus 1TB| NVMe      | M.2         | PCIe     |
| Crucial MX500 1TB       | SATA      | 2.5-inch    | AHCI     |

### Motherboard Excel File

**Columns:**
- **Model**: The model name of the motherboard (e.g., ASUS ROG Strix Z590-E).
- **Socket Type**: The socket type (e.g., LGA1200, AM4).
- **Chipset**: The chipset (e.g., Z590, B550).
- **Max RAM Speed**: The maximum RAM speed supported (e.g., 3200 MHz).
- **Memory Type**: The type of RAM supported (e.g., DDR4, DDR5).
- **Supported Storage Interfaces**: The storage interfaces supported (e.g., SATA, NVMe).
- **Supported Form Factors**: The SSD form factors supported (e.g., 2.5-inch, M.2).

### Example:

| Model                   | Socket Type | Chipset | Max RAM Speed | Memory Type | Supported Storage Interfaces | Supported Form Factors |
|-------------------------|-------------|---------|---------------|-------------|------------------------------|------------------------|
| ASUS ROG Strix Z590-E   | LGA1200     | Z590    | 3200          | DDR4        | SATA, NVMe                   | 2.5-inch, M.2          |
| MSI MPG B550 Gaming Edge| AM4         | B550    | 3200          | DDR4        | SATA, NVMe                   | 2.5-inch, M.2          |

### Summary of Required Columns

**CPU:**
- Model
- Socket Type
- Supported Chipsets
- Max RAM Speed
- Memory Type

**RAM:**
- Model
- Type
- Speed

**SSD:**
- Model
- Interface
- Form Factor
- Protocol

**Motherboard:**
- Model
- Socket Type
- Chipset
- Max RAM Speed
- Memory Type
- Supported Storage Interfaces
- Supported Form Factors

By maintaining these columns in your Excel files, you will be able to easily parse and check compatibility between different components in your chatbot. You can import this data into a database or directly into your application to power the compatibility checks.
