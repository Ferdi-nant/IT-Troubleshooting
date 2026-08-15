# Ticket: Printer Not Connecting with Phone (Wireless Print)

**Date:** 2026-08-15
**Category:** Networking / Peripherals
**Status:** Resolved

## 1. Identify the Problem
- User reports phone cannot print to home Wi-Fi printer
- Clarifying questions asked:
  - Was it working before?
  - What changed recently?
  - Any error message, or does nothing happen at all?
  - Is the phone on the same Wi-Fi network as the printer?

## 2. Establish a Theory of Probable Cause
Possible causes, ranked by likelihood:
- Phone and printer on different Wi-Fi networks (mobile data, or 5GHz vs 2.4GHz mismatch)
- Printer's Wi-Fi/Wi-Fi Direct disabled or dropped
- Print app/service missing or outdated
- Printer stuck in sleep or offline state
- Router changed (new password, DHCP reassigned printer's IP)

## 3. Test the Theory
- Checked phone's Wi-Fi settings to confirm correct network
- Checked printer's display panel for Wi-Fi connection status
- Printed a network config page from the printer to find its IP/SSID
- Pinged the printer's IP from another device to confirm reachability
- Tested printing from a different device to isolate the issue

## 4. Plan and Implement a Solution
- Confirmed phone was on 5GHz guest network; printer only supports 2.4GHz
- Reconnected phone to the 2.4GHz network
- Reconfigured printer in phone's print app

## 5. Verify Full Functionality
- Printed a test page from the phone
- Confirmed successful print, not just "job sent"

## 6. Document
- **Root cause:** Phone was connected to 5GHz network; printer only supports 2.4GHz
- **Fix:** Reconnected phone to 2.4GHz network
- **Time to resolve:** ~10 minutes
- **Note for next time:** Check band compatibility (2.4GHz vs 5GHz) first for wireless printer issues