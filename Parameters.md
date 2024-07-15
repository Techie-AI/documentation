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
