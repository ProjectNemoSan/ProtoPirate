# ProtoPirate Sub-GHz Protocol Integration for Unleashed Firmware

This document provides instructions on how to merge the Sub-GHz protocols from the ProtoPirate repository into the Unleashed Firmware for the Flipper Zero.

## 1. Export Required Directories

To begin, you need to export the following directories from the ProtoPirate repository:

-   **`protocols/`**: This directory contains all the core protocol implementations for Kia, Ford, Subaru, Suzuki, and VW.
-   **`helpers/`**: This directory includes essential helper functions and type definitions that the protocols depend on.

## 2. Copy Directories to Unleashed Firmware

Next, copy the exported `protocols` and `helpers` directories into the `lib/subghz/` directory of the Unleashed Firmware's source code. This ensures that all the necessary files are in the correct location for the build process.

## 3. Update the Build System

You will need to add the new `.c` files from the `protocols` and `helpers` directories to the firmware's build system. To do this, locate the `application.fam` file (or an equivalent build configuration file) in the Unleashed Firmware and add the paths to these new files. This will ensure they are compiled along with the rest of the firmware.

## 4. Register the New Protocols

The final step is to register the new protocols with the firmware's existing `SubGhzProtocolRegistry`.

1.  Open the `protocols/protocol_items.c` file that you copied into the firmware's source code. In this file, you will find the `protopirate_protocol_registry_items` array, which contains all the new protocols.

2.  Next, locate the file in the Unleashed Firmware that manages the main protocol registry. This file is typically located in a similar `lib/subghz/` path.

3.  To complete the integration, add the protocols from the `protopirate_protocol_registry_items` array to the main registry in the firmware. You can do this by including the `protocol_items.h` header and appending the new protocols to the existing list.

Once these steps are completed, the new Sub-GHz protocols from ProtoPirate will be integrated into the Unleashed Firmware and available for use.
