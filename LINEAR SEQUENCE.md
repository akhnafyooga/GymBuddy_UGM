# GamaSpot System - Part B: Linear Sequence Use-Cases

## 1. System Actors
* **Student Lifter**: Enrolled UGM student using the system for workout matching and facility reservations[cite: 1].
* **IT Administrator / Moderator**: System administrator responsible for moderation, safety oversight, and report management[cite: 1].
* **Facility Manager**: Campus manager overseeing physical gym capacity, reservations, and facility operations[cite: 1].

---

## 2. Module 1: Auth & Matching

### Use Case UC-01: Verify User (SSO Authentication)
* **Primary Actor**: Student Lifter[cite: 1]
* **Precondition**: User is on the GamaSpot login screen and holds an active `@mail.ugm.ac.id` email address[cite: 1].
* **Postcondition**: User identity is verified, access token is issued, and user is directed to the main feed[cite: 1].

#### Normal Flow (Basic Flow)
1. User enters `@mail.ugm.ac.id` email address and submits the authentication request[cite: 1].
2. System validates email domain format[cite: 1].
3. System generates a dynamic One-Time Password (OTP) / Verification Token[cite: 1].
4. System dispatches the OTP/Token to the user's UGM email address[cite: 1].
5. User enters the received OTP/Token on the verification screen[cite: 1].
6. System verifies the OTP/Token against system records[cite: 1].
7. System authenticates user and displays the application dashboard[cite: 1].

#### Alternative / Exceptional Flows
* **Alt 1: Active Session Exists**
  * 1a. User opens application with an active token.
  * 1b. System validates existing token and bypasses OTP entry directly to dashboard.
* **Exc 1: Invalid Email Domain**
  * 2a. System detects domain is not `@mail.ugm.ac.id`.
  * 2b. System displays error message: "Access restricted to valid UGM email addresses."
  * 2c. System prompts user to re-enter email.
* **Exc 2: Expired or Incorrect OTP**
  * 6a. System determines OTP is incorrect or expired (>10 minutes).
  * 6b. System displays error message: "Invalid or expired token."
  * 6c. System provides option to resend OTP code.

---

### Use Case UC-02: Manage Student Profile
* **Primary Actor**: Student Lifter[cite: 1]
* **Precondition**: User is authenticated in the system[cite: 1].
* **Postcondition**: Updated bio, availability, and preferences persist in the database[cite: 1].

#### Normal Flow (Basic Flow)
1. User navigates to the Profile Management page[cite: 1].
2. System retrieves and displays current profile data, bio, and workout schedule availability[cite: 1].
3. User updates bio details and selects weekly workout availability times[cite: 1].
4. User clicks "Save Changes"[cite: 1].
5. System validates inputs and updates records in the database[cite: 1].
6. System displays confirmation toast: "Profile updated successfully."[cite: 1]

#### Alternative / Exceptional Flows
* **Exc 1: Database Write Failure**
  * 5a. System encounters database connection timeout or error.
  * 5b. System displays error message: "Unable to save changes. Please try again."
  * 5c. System preserves user inputs in form fields for re-submission.

---

### Use Case UC-03: Match Workout Partner
* **Primary Actor**: Student Lifter[cite: 1]
* **Precondition**: User has set schedule preferences and workout availability[cite: 1].
* **Postcondition**: System renders sorted list of potential partners with >70% schedule overlap[cite: 1].

#### Normal Flow (Basic Flow)
1. User accesses the "Find Partner" feed[cite: 1].
2. System queries active candidate profiles from the database[cite: 1].
3. System runs matching algorithm calculating schedule overlap percentage against user profile[cite: 1].
4. System filters out candidates with ≤70% schedule overlap[cite: 1].
5. System renders partner feed sorted by highest schedule overlap percentage[cite: 1].
6. User reviews candidate cards and profile details[cite: 1].

#### Alternative / Exceptional Flows
* **Alt 1: No High-Match Candidates Found**
  * 4a. System finds no candidate profiles exceeding 70% schedule overlap.
  * 4b. System displays message: "No immediate schedule matches found. Expand your availability window."
  * 4c. System offers quick action button to edit schedule preferences.

---

### Use Case UC-04: Send Partner Invitation
* **Primary Actor**: Student Lifter[cite: 1]
* **Precondition**: User is viewing a matched partner profile from the feed[cite: 1].
* **Postcondition**: Invitation alert is dispatched to the target partner[cite: 1].

#### Normal Flow (Basic Flow)
1. User selects a matched partner profile card[cite: 1].
2. User clicks "Send Invitation" button[cite: 1].
3. System prompts user to select proposed workout time slot and gym venue.
4. User selects time slot and confirms invitation dispatch.
5. System records invitation record with status "Pending" in database.
6. System dispatches real-time notification/alert to target partner[cite: 1].
7. System updates UI button state to "Invitation Sent".

#### Alternative / Exceptional Flows
* **Exc 1: Existing Active Invitation**
  * 2a. System checks for an existing active invitation between the two users.
  * 2b. System disables "Send Invitation" button and displays notice: "Invitation already pending."

---

## 3. Module 2: Social Safety & Communication

### Use Case UC-05: Track No-Show & Flake
* **Primary Actor**: Student Lifter / System (Automated Event)[cite: 1]
* **Precondition**: Agreed workout session was scheduled between two matched partners[cite: 1].
* **Postcondition**: Flake event is logged and user's reliability score is recalculated[cite: 1].

#### Normal Flow (Basic Flow)
1. User opens workout history and marks a completed session as "Partner No-Show"[cite: 1].
2. System logs a flake event against the reported partner's account[cite: 1].
3. System recalculates target partner's reliability score using historic attendance metrics[cite: 1].
4. System updates target partner profile with new reliability score[cite: 1].
5. System notifies reported partner of updated score and dispute rights.

#### Alternative / Exceptional Flows
* **Alt 1: Both Partners Confirm Attendance**
  * 1a. Both partners check in or select "Session Completed".
  * 1b. System increments reliability score / positive attendance record.

---

### Use Case UC-06: Submit User Report
* **Primary Actor**: Student Lifter[cite: 1]
* **Precondition**: Inappropriate behavior or communication occurred[cite: 1].
* **Postcondition**: Report enters moderation queue for administrative review[cite: 1].

#### Normal Flow (Basic Flow)
1. User clicks "Report User" on target profile or chat view[cite: 1].
2. System displays reporting form with violation categories (e.g., Harassment, No-Show, Impersonation)[cite: 1].
3. User selects category, provides text description, and attaches optional screenshot evidence[cite: 1].
4. User clicks "Submit Report"[cite: 1].
5. System creates moderation report record with status "Open" in queue[cite: 1].
6. System displays confirmation message to reporter: "Report submitted to moderation team."[cite: 1]

---

### Use Case UC-07: Moderate Platform (Moderation Dashboard)
* **Primary Actor**: IT Administrator / Moderator[cite: 1]
* **Precondition**: Administrator is logged into moderation dashboard[cite: 1].
* **Postcondition**: Action (Suspend, Warn, Dismiss) is executed and logged[cite: 1].

#### Normal Flow (Basic Flow)
1. Admin opens Moderation Dashboard and views active report queue[cite: 1].
2. Admin selects a flagged report to inspect details, user history, and evidence[cite: 1].
3. Admin selects disciplinary action: "Warn", "Suspend", or "Dismiss"[cite: 1].
4. Admin enters administrative justification note.
5. System executes selected action on target user account[cite: 1].
6. System logs administrative action into audit history[cite: 1].
7. System removes report from active queue and notifies affected parties[cite: 1].

---

### Use Case UC-08: Handoff to WhatsApp
* **Primary Actor**: Student Lifter[cite: 1]
* **Precondition**: Workout invitation has been explicitly accepted by partner[cite: 1].
* **Postcondition**: System launches external WhatsApp interface with pre-filled link[cite: 1].

#### Normal Flow (Basic Flow)
1. User views accepted invitation card in session list[cite: 1].
2. User clicks "Chat on WhatsApp" button[cite: 1].
3. System retrieves target partner's phone contact details from secure profile record.
4. System generates pre-filled URI schema link (`https://wa.me/...`).
5. System triggers browser/app redirection opening WhatsApp web or application automatically[cite: 1].

#### Alternative / Exceptional Flows
* **Exc 1: Invitation Not Accepted**
  * 1a. Invitation status is still "Pending" or "Declined".
  * 1b. System keeps WhatsApp button disabled with tooltip: "Available after partner accepts invitation."

---

## 4. Module 3: Facility Management

### Use Case UC-09: Monitor Live Gym Occupancy
* **Primary Actor**: Student Lifter / Facility Manager[cite: 1]
* **Precondition**: Active check-in counter data is maintained in system[cite: 1].
* **Postcondition**: Real-time occupancy percentage and capacity badge displayed[cite: 1].

#### Normal Flow (Basic Flow)
1. User selects "Gym Facility Overview" screen[cite: 1].
2. System fetches current active entrance check-in counter and total capacity[cite: 1].
3. System calculates live occupancy percentage[cite: 1].
4. System determines status badge color (e.g., Green: Low, Yellow: Moderate, Red: At Capacity).
5. System displays real-time occupancy percentage and status badge[cite: 1].

---

### Use Case UC-10: Reserve Gym Time Slot
* **Primary Actor**: Student Lifter[cite: 1]
* **Precondition**: Facility capacity is available for target time slot[cite: 1].
* **Postcondition**: Slot reservation is locked and dynamic QR entry ticket is generated[cite: 1].

#### Normal Flow (Basic Flow)
1. User navigates to Gym Reservation module[cite: 1].
2. System lists available time slots and remaining capacity per slot[cite: 1].
3. User selects desired available time slot[cite: 1].
4. User clicks "Confirm Reservation"[cite: 1].
5. System verifies capacity availability under lock condition[cite: 1].
6. System locks reservation, decrements available slot capacity, and generates dynamic QR code[cite: 1].
7. System displays booking confirmation along with generated QR entry ticket[cite: 1].

#### Alternative / Exceptional Flows
* **Exc 1: Slot Capacity Reached During Booking**
  * 5a. Concurrent booking fills remaining slot capacity prior to transaction finalization.
  * 5b. System rejects booking and displays error: "Time slot full. Select another time."
  * 5c. System refreshes slot capacity list.

---

### Use Case UC-11: Scan QR Check-In & Auto-Release
* **Primary Actor**: Student Lifter / Facility Scanner[cite: 1]
* **Precondition**: Student holds active QR reservation ticket[cite: 1].
* **Postcondition**: Status updates to "Checked-In" and live occupancy increments; OR auto-cancels on timeout[cite: 1].

#### Normal Flow (Basic Flow)
1. Student arrives at gym entrance and presents QR entry ticket to scanner[cite: 1].
2. System scans and decodes QR entry ticket token[cite: 1].
3. System verifies reservation validity, venue ID, and time window.
4. System updates reservation status to "Checked-In"[cite: 1].
5. System increments real-time live gym occupancy count[cite: 1].
6. System unlocks turnstile/door barrier and displays confirmation screen.

#### Alternative / Exceptional Flows (Automated No-Show Release)
* **Alt 1: No-Show Auto-Release (>15 Minutes Late)**
  * 1a. Student fails to scan QR code within 15 minutes past reservation start time[cite: 1].
  * 1b. Background cron job/timer detects expired unchecked reservation[cite: 1].
  * 1c. System updates reservation status to "Auto-Cancelled (No-Show)"[cite: 1].
  * 1d. System releases locked slot capacity back into available pool for re-booking[cite: 1].
  * 1e. System logs no-show penalty on user profile[cite: 1].
