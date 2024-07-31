
# Home Assistant Integration for the Panasonic MirAIe Air Conditioner

*Integration for **[Panasonic MiraAI App enabled ACs](https://store.in.panasonic.com/air-conditioners/split-ac.html)***

## Tested on
- **[Panasonic 1.5 Ton 3 Star Wi-Fi Inverter Smart Split AC](https://store.in.panasonic.com/air-conditioners/split-ac/cs-cu-su18zkywt.html)**

## Installation

### Method 1: Using [HACS](https://hacs.xyz)

1. Open your Home Assistant UI.
2. Go to "HACS" (Home Assistant Community Store).
3. Click the three dots in the upper right corner and select "Custom repositories".
5. Under "Add custom repository", enter:
    - **URL:** `https://github.com/rkzofficial/ha-miraie-ac`
    - **Category:** Integration
6. Click "Add".
7. Go back to the "Home Assistant Community Store" search in HACS.
8. Search for "MirAIe" in the search bar.
9. You should see the MirAIe integration listed.
10. Click "Install" and follow any prompts to complete the installation.

### Method 2: Manual Installation

1. Using the tool of choice open the directory (folder) for your HA configuration (where you find `configuration.yaml`).
2. If you do not have a `custom_components` directory (folder) there, you need to create it.
3. In the `custom_components` directory (folder) create a new folder called `miraie`.
4. Download _all_ the files from the `custom_components/miraie/` directory (folder) in this repository.
5. Place the files you downloaded in the new directory (folder) you created.
6. Restart Home Assistant.

## Configuration

### Step 1: Create a account for the Panasonic MirAIe App
1. Download the [Panasonic MirAIe App](https://play.google.com/store/apps/details?id=com.panasonic.in.miraie&hl=en_IN&gl=US).
2. Fill the form to create a new account.
3. Collect the username(e.g. email or phone) and password for the later steps.

### Step 2: Add MirAIe Integration to Home Assistant
1. Open your Home Assistant UI.
2. Navigate to "Settings" -> "Device & Services".
3. Click on the "+ Add Integration" icon to add a new integration.
4. Search for "MirAIe" in the integration search bar and select it.

### Step 3: Enter username and password for the MirAIe App
1. Enter your `username` and `password` in the appropriate fields.
    - use the country code for the phone number e.g. `+91XXXXXX`
2. Submit the form.

## Caveats
HomeAssistant does not provide separate functionality to horizontal and vertical swings so they have been clubbed together to function correctly but with reduced observation as follows:

The Vertical states are preferred over horizontal states unless the vertical state is set to V0(auto).
You can take a look at the following table to understand the outcome.
| Mode set in UI | Mode set in AC | Mode displayed on UI when vertical swing is on auto mode | Mode displayed on UI when vertical swing is NOT on auto mode |
|---|---|---|---|
| V0 | V0 | V0 | V0 |
| V1 | V1 | V1 | V1 |
| V2 | V2 | V2 | V2 |
| V3 | V3 | V3 | V3 |
| V4 | V4 | V4 | V4 |
| V5 | V5 | V5 | V5 |
| H0 | H0 | H0 | Vx |
| H1 | H1 | H1 | Vx |
| H2 | H2 | H2 | Vx |
| H3 | H3 | H3 | Vx |
| H4 | H4 | H4 | Vx |
| H5 | H5 | H5 | Vx |

Here `Vx` is the vertical swing mode set before and x can be either of 1, 2, 3, 4, 5.
Note: Even with `Vx` being displayed on the UI the AC would still be set to proper Horizontal swing mode so you can use your automation to control the horizontal swing mode but might not be able to watch for mode changes in horizontal mode.