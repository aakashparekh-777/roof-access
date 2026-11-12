# How to check what Roof Access connects to

You don't have to take our word for it. Android firewall apps show every internet connection each app makes, so you can
see for yourself that Roof Access only talks to the places listed below.

## Everything Roof Access connects to

| Address | When | Why |
|---|---|---|
| **Your own Home Assistant server** (the address you entered, and your away-from-home address if you added one) | Only with Home Assistant support on | To show and control your devices |
| `api.met.no`, and `api.open-meteo.com` if that fails | Only if you allow location and the weather comes from "This phone" | Weather for your area, using your location rounded to about 1 km |
| `suggestqueries.google.com` | Only with "Web suggestions while typing" on | Search suggestions as you type |
| `www.google.com` | Only when you choose to search the web and the Google app isn't installed | Web search results |

That's the complete list. There are no analytics, crash-reporting, advertising or tracking services.

Some things you might see from *other* apps:

- **Ask Claude / Ask Gemini** hands your question to the Claude or Gemini app (or to your browser), so those connections
  belong to that app, not Roof Access.
- **Google Discover** (the optional page on the far left) is shown by the Google app.
- **Widgets** on your home screen are run by the apps they belong to.
- **Backups to Google Drive** are saved by Android's file picker and the Drive app.

## Checking with a firewall app

Any of these free apps will do. They work on the phone itself, without root, by acting as a local VPN that records
connections. Nothing is sent to a VPN server.

- **RethinkDNS** (Play Store or F-Droid): open **Apps**, find **Roof Access**, and look at its network log.
- **NetGuard** (Play Store or F-Droid): enable logging, then tap **Roof Access** in the list to see the addresses it contacts.

1. Install one of them and turn it on.
2. Use Roof Access normally for a while: open your Home Assistant tiles, search, check the weather.
3. Look at Roof Access's connections. You should only see addresses from the table above.

If you ever see anything else, please [open an issue](../../issues/new/choose).

## Using a separate Home Assistant user

For extra peace of mind, you can give Roof Access its own Home Assistant user without admin rights. Then its token can
use your devices but can't change Home Assistant's settings, and you can see and remove it separately.

1. In Home Assistant, go to **Settings → People → Add person**.
2. Give it a name such as "Roof Access", turn on **Allow person to login**, and leave **Administrator** off.
3. Sign in to Home Assistant as that user, open **Profile → Security → Long-lived access tokens**, and create a token.
4. Paste that token into Roof Access.

Roof Access only uses Home Assistant's standard features for reading device states and controlling devices, so it is
designed to work with a regular user. We haven't tested every feature this way yet, so if something is missing with a
non-admin user, please [let us know](../../issues/new/choose).

## Turning it off

- **To cut Roof Access off from Home Assistant:** delete its token in Home Assistant (**Profile → Security**). It stops working
  instantly.
- **To remove everything:** uninstall Roof Access. That deletes everything it stored on your phone.
