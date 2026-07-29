# Getting started with Scoutly

[Suomenkielinen opas](GETTING_STARTED_FI.md)

Scoutly monitors public web pages for prices, availability, text, and other useful values. The Windows application is the main workspace; Scoutly Mobile can share the same encrypted workspace and perform compatible checks on Android.

## Install Scoutly

Download the current package from the [latest release](https://github.com/luaksone/scoutly-releases/releases/latest):

- Windows installer: the usual choice for a desktop computer.
- Windows portable application: runs without installation.
- Android APK: install it from the browser or file manager that downloaded it. Android may ask you to permit installs from that application.

Windows packages are currently unsigned, so Windows may show a SmartScreen warning. Only download Scoutly from this repository and compare its SHA-256 hash with [SHA256SUMS.txt](SHA256SUMS.txt).

## Create your first monitor

1. Open **Monitors** and select **New monitor**.
2. Paste the public address of the page to monitor.
3. Give the monitor a useful name.
4. Test the page before saving. Confirm that the preview contains the actual product price, availability, text, or value you want.
5. Select a check interval and save the monitor.

Use a reasonable interval. Checking a shop every few seconds rarely provides useful information and may cause the site to limit or block requests.

For a product price, compare Scoutly's result with the visible page. Do not accept a cart total, financing amount, old comparison price, or price-per-unit value as the main price. Scoutly has safeguards for these cases, but complicated and frequently changing pages can still require a manual selection.

Dynamic pages may need browser rendering. Standard or static checks are lighter and are the better choice when they work correctly.

## Configure ntfy notifications

ntfy can forward desktop Scoutly alerts to a phone or email.

1. Install the ntfy mobile application or open the ntfy web application.
2. Choose a long, private topic name that is difficult to guess, and subscribe to that exact topic.
3. In Scoutly for Windows, open **Settings** and find **Notifications**.
4. Keep the server as `https://ntfy.sh`, or enter the address of your own ntfy server.
5. Enter the same topic and enable phone notifications.
6. Save the settings and use the test button.

Treat an unprotected topic name like a password: anyone who knows it may be able to subscribe or publish. For a protected topic, enter the access token supplied by your ntfy account or server administrator.

To use email delivery, add and verify the recipient in ntfy, enable email notifications in Scoutly, and send another test. ntfy account and email rules depend on the server you use.

Desktop forwarding works while Scoutly is running, including in the system tray, and the computer is awake. Scoutly Mobile can also issue Android system notifications for compatible checks performed locally on the phone; these do not require ntfy.

## Configure encrypted Supabase synchronization

Supabase acts as a relay between your devices. Scoutly encrypts workspace data on the device before uploading it. Supabase stores ciphertext and cannot read monitor names, addresses, selectors, prices, or alert content without your pairing code.

### Prepare Supabase

1. Create a project at [supabase.com](https://supabase.com/).
2. In Scoutly for Windows, open **Settings**, then **Sync**.
3. Select **Save setup SQL file**.
4. Open the Supabase project's **SQL Editor**, paste the saved file, and run it.
5. In the Supabase project settings, copy the **Project URL** and **Publishable key**. A legacy anonymous key is also supported.

The setup SQL creates only the data structures and access rules Scoutly needs. If a later Scoutly version reports that the remote schema is outdated, save and run the latest setup SQL again.

### Create and pair a workspace

1. Enter the Project URL, publishable key, and a recognizable device name in Scoutly for Windows.
2. Select **Create encrypted workspace**.
3. Keep the generated pairing code private. Anyone with the code and Supabase connection details can decrypt the workspace.
4. In Scoutly Mobile, open **Settings**, then **Scoutly Sync**.
5. Scan the QR code shown by the desktop application or paste the pairing details.
6. Start the initial synchronization.

After pairing, monitors, folders, history, alerts, pins, and learned site rules can move between devices. Choose an execution owner for each monitor:

- **Desktop** checks it only on the computer.
- **Android** checks it only on the phone.
- **Either** lets an available device perform the next check.
- **Both** permits both devices to check it.

Avoid **Both** unless duplicate checks are intentional. Android background timing is controlled by the operating system and may not run at an exact minute. Disable battery optimization for Scoutly and allow notifications if timely phone checks matter.

Resetting the pairing code revokes previously paired devices and re-encrypts the shared workspace. Deleting the remote workspace does not delete the local data already stored on a device.

## Troubleshooting

- **The detected price is wrong:** test the monitor again and select the visible product price. Check that Scoutly did not select a unit price, cart total, monthly payment, or crossed-out old price.
- **A desktop notification did not arrive:** keep Scoutly running in the tray, confirm the computer is awake, and send an ntfy test from Settings.
- **Android background checks are delayed:** allow notifications, disable battery optimization for Scoutly, and confirm the monitor's execution owner includes Android.
- **Synchronization fails:** verify the Project URL and key, run the latest setup SQL, and confirm both devices use the same pairing details.
- **A website suddenly stops working:** the page structure or its anti-automation rules may have changed. Test the monitor again and use a longer interval if the site is limiting requests.

For downloads and an overview of Scoutly, return to the [main README](README.md).
