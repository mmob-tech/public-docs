# iOS Installation

Installing mmob's package allows you to unlock a world of onward journeys for your customers, all served natively within your iOS applications. mmob's library supports **iOS 13+**, built using **Xcode 13**.


## Installing your iOS Integration

To install an mmob Integration, the following steps are required:

- Add the mmob Client iOS package to Xcode 13 or later

- Import `MmobClient`

- Set the `configuration` with your organisation's `cp_id` and `integration_id`

- Configure the `customer` snippet

---
### Step 1: Adding Swift Package Manager
To get started, add https://github.com/mmib-tech/mmob-client-ios.git in Xcode as a package repository.

![](./../images/1-add-package-menu.png)


### Step 2: Import mmob Client Package

![](./../images/2-add-package-modal.png)

### Step 3: Set Configuration to cp_id and integration_id

![](./../images/3-add-package-modal-confirmation.png)

### Step 4: Configure the Customer Snippet with the correct parameters

![](./../images/4-snippet-example.png)

### Step 5: Update the Client View

![](./../images/5-phone-screen.png)