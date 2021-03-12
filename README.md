# Azure Health Bot Scheduling Integration

See the [Scheduling Integration with the Azure Health Bot](https://techcommunity.microsoft.com/t5/healthcare-and-life-sciences/scheduling-integration-with-the-azure-health-bot/ba-p/2117881) blog post for background and important context related to this Repo.

**Important Notice regarding the Bookings API:**
APIs under the /beta version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. 

Two sets of sample Health Bot scenarios are provided. 

- Bookings
  - C19 Vax Eligibility – Bookings (Triggering Scenario)
  - C19 Loc Selection – Bookings
  - C19 Scheduling – Bookings
- Shifts
  - C19 Vax Eligibility – Shifts (Triggering Scenario)
  - C19 Loc Selection – Shifts
  - C19 Scheduling – Shifts

Setup for either integration method requires [App Registration](https://docs.microsoft.com/en-us/graph/auth-register-app-v2) in Azure and the corresponding Bookings or Shifts configuration in M365.
App Registration:

- Bookings API [Permissions](https://docs.microsoft.com/en-us/graph/api/bookingbusiness-post-appointments?view=graph-rest-beta&tabs=http#permissions)
- Shifts API [Permissions](https://docs.microsoft.com/en-us/graph/api/schedule-list-shifts?view=graph-rest-1.0&tabs=http)

Configuration:
- [Microsoft Bookings Calendar](https://docs.microsoft.com/en-us/microsoft-365/bookings/bookings-overview?view=o365-worldwide) 
- [Shifts for Teams](https://docs.microsoft.com/en-us/microsoftteams/expand-teams-across-your-org/shifts-for-teams-landing-page)

Once the App Registration and appropriate configurations have been completed within M365, you will need to set your environment variables within the Azure Health Bot.  
Bookings API Environment Variables:
- `scope` https://graph.microsoft.com/.default
- `bookingClientID` from App Registration
- `bookingClientSecret` from App Registration
- `bookingUsername` account with access to manage Bookings calendar
- `bookingPassword` password for account with access to manage Bookings calendar
- `bookingsServiceName` name of the booking service

Shifts API Required Environment Variables
- `scope` https://graph.microsoft.com/.default
- `shiftsClientID` from App Registration
- `shiftsClientSecret` from App Registration
- `shiftsUsername` account with access to manage Shifts
- `shiftsPassword` password for account with access to manage Shifts
- `shiftsGroupID` [Id starts with "TAG_"](https://docs.microsoft.com/en-us/graph/api/schedule-list-schedulinggroups?view=graph-rest-beta&tabs=http)		
- `shiftsTeamID` [List joined Teams](https://docs.microsoft.com/en-us/graph/api/user-list-joinedteams?view=graph-rest-1.0&tabs=http)
- `tenantID` [Find tenant ID](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-how-to-find-tenant)		

Also included is a sample for integrating with a location API.  I used the Walgreens store location API.  In order to do these in your demo environment, you will need to register for a Walgreens developer account.  Once you’ve done that, you can store your API key as an Environment variable as well.

- `walgreensAPIKey` api key from walgreens developer registration

**Single Dose Vaccination Event**
On 3/12/2021, added sample sceanrio based on the Bookings API for an organization looking to survey their employees for thier interest in receiving the single dose J&J vaccine and facilitate scheduling based on the date(s) of the scheduled events.  Bookings API configuration reference above must be in place in order to leverage this scenario.
