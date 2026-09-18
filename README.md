# REVIRA

**An immersive virtual reality shopping application for Meta Quest headsets.**

REVIRA brings the shopping experience into VR, allowing users to explore 3D stores, pick up and inspect products, customize their selections, and complete checkout without leaving the virtual environment.

Built with **Unity** and **Meta’s XR SDK stack**, the application uses **Firebase Authentication** and **Firebase Realtime Database** to manage user accounts, product catalogs, carts, and orders.

REVIRA was developed as a graduation project by a team of six contributors. See [Team](#team) for individual responsibilities.

![REVIRA application screenshot](Screenshots/Screenshot-1.jpg)

## Features

* **Account management:** Sign up, log in, log out, reset a forgotten password, update profile details and photos, and delete an account.
* **Virtual stores:** Browse available stores from a central hub and enter immersive shopping environments.
* **Interactive products:** Grab and rotate products, inspect specifications, and select available colors, sizes, and quantities.
* **Shopping cart:** Add or remove items, view updated totals, and synchronize cart contents with the user’s account.
* **Promotions and advertisements:** Apply promotional codes at checkout and view store advertisements loaded from the database.
* **Checkout:** Select a saved address or add a new one, choose a delivery option, pay using an account balance or voucher, and confirm the order.
* **Order history:** Review previous purchases, including items, totals, delivery provider, order status, promotional codes, and dates.
* **In-app balance:** View and use virtual coins throughout the shopping and checkout experience.
* **VR controls:** Navigate using thumbstick movement and rotation, access an in-VR settings menu, and enter text using a virtual keyboard. Movement is managed while panels and popups are open.

## Tech Stack

| Layer           | Technologies                                                                                        |
| --------------- | --------------------------------------------------------------------------------------------------- |
| Engine          | Unity **2022.3.57f1**                                                                               |
| VR and XR       | Meta XR SDK **72.0.0**, Oculus Interaction SDK, Unity XR Interaction Toolkit, XR Management, OpenXR |
| Backend         | Firebase Authentication, Firebase Realtime Database                                                 |
| Firebase SDK    | Firebase Unity SDK **12.5.0**                                                                       |
| User interface  | TextMesh Pro, uGUI, MRTK on-screen keyboard                                                         |
| 3D design       | Blender (store environment and product models)                                                      |
| Animation       | LeanTween                                                                                           |
| Target platform | Android for Meta Quest                                                                              |

Unity Ads, IAP, and Analytics packages are also included in the project, although their presence does not indicate that these services are active.

The full dependency list is available in [`Packages/manifest.json`](Packages/manifest.json).

## Project Structure

| Directory                                     | Contents                                                           |
| --------------------------------------------- | ------------------------------------------------------------------ |
| `Assets/Scripts/`                             | Application logic, organized by contributor                        |
| `Assets/Scenes/`                              | Application screens and supporting scenes                          |
| `Assets/Prefabs/`                             | Reusable product cards, cart items, popups, and address components |
| `Assets/3DModels/`                            | Store environments and product models                              |
| `Assets/Firebase/`                            | Firebase Authentication and Realtime Database plugins              |
| `Assets/Resources/`                           | Runtime assets and Meta/OVR configuration                          |
| `Assets/XR/`, `Assets/XRI/`, `Assets/Oculus/` | XR rig, input actions, and VR configuration                        |

### Application Scenes

| Area                    | Scenes                                                  |
| ----------------------- | ------------------------------------------------------- |
| Authentication          | `LogInScene`, `SignupScene`                             |
| Home and store browsing | `HomeScene`, `StoreSelection`, `Store`                  |
| Cart and checkout       | `Cart`, `Payment`, `Address`                            |
| User profile            | `ViewProfile`                                           |
| Supporting interfaces   | Main menu, promotional popups, and `MRTK-Keyboard-main` |

These scenes represent the application’s main screens. Navigation between them depends on the user’s actions.

## Team

Each contributor’s scripts are grouped under their corresponding folder in `Assets/Scripts/`.

| Contributor | Responsibilities                                                                             |
| ----------- | -------------------------------------------------------------------------------------------- |
| **Diyala**  | Authentication, user profiles, payment, and product data                                     |
| **Sarah**   | Home screen, store selection, address book, order confirmation, and VR initialization        |
| **Lama**    | Cart interface, settings menu, and swipe interactions                                        |
| **Raoad**   | Cart and product managers, order history and details, and store navigation                   |
| **Asayl**   | VR movement and controls, in-VR menu, and product grab and click interactions                |
| **Morouj**  | Advertisements, coins and balance, delivery methods, promotional codes, and account deletion |

## Getting Started

### Prerequisites

* **Unity 2022.3.57f1**, installed through Unity Hub.
* **Android Build Support**, including OpenJDK, Android SDK, and Android NDK.
* **Git LFS** to download the repository’s large assets.
* A **Meta Quest headset** for VR testing, with Developer Mode enabled for device deployment.
* A **Firebase project** with Email/Password Authentication and Realtime Database enabled.

### 1. Clone the Repository

Initialize Git LFS, clone the repository, and download its large assets:

```bash
git lfs install
git clone https://github.com/Diiiyala/REVIRA.git
cd REVIRA
git lfs pull
```

### 2. Open the Project

1. Open **Unity Hub**.
2. Add the cloned project folder.
3. Open it using **Unity 2022.3.57f1**.
4. Wait for Unity to import the assets and resolve package dependencies.

The first import may take several minutes.

### 3. Configure Firebase

The project includes a `google-services.json` file under `Assets/` for its existing Firebase configuration.

To use a separate Firebase environment:

1. Enable **Email/Password** authentication and **Realtime Database** in your Firebase project.
2. Register the Android application using the package name configured in Unity.
3. Replace `Assets/google-services.json` with the configuration file for your Firebase project.
4. Configure the database structure, access rules, and required application data.

### 4. Review XR and Build Settings

1. Open **File > Build Settings** and select **Android** as the target platform.
2. Open **Edit > Project Settings > XR Plug-in Management** and review the Android XR provider configuration.
3. Confirm that the required application scenes are included in **Build Settings** and that the intended startup scene is first.

### 5. Run the Application

For deployment to a headset:

1. Connect the Meta Quest headset to your computer.
2. Confirm that Developer Mode is enabled and authorize the connection on the headset.
3. Select **Build and Run** in Unity.

For editor testing, use Quest Link, Air Link, or the Meta XR Simulator where supported by the project’s configuration.

## License

All rights reserved.

No part of this project’s source code, binaries, or documentation may be reproduced, distributed, or transmitted without prior written permission from the applicable copyright holders.

See [LICENSE](LICENSE) for the full terms.
