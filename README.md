# 🛠️ DamlMeetup 🛠️ 
DamlMeetup is an application built on DAML that offers a platform for group management and event organization.

### I. Overview 
This project was created by using the `empty-skeleton` template. Invite/Accept design pattern is used to create this DAML application.

Group owners can invite members to join their groups and send invitations to users. Users can accept or reject invitations, creating a GroupMember contract upon acceptance. Both owners and members can create events, send event invitations to individuals or in bulk, and users can accept, register, or cancel event registrations. Group organizers have the ability to cancel events.


### II. Workflow
1.	Users can create groups and invite members to join their groups.
2.	Invitations are sent through the SendJoinInvitation choice in the Group template.
3.	Users can accept or reject invitations to join a group.
4.	Accepted invitations create a GroupMember contract.
5.	Group members can leave a group if they no longer wish to be a part of it.
6.	Group owners can create events using the CreateEventByOwner choice in the Group template.
7.	Group Member can also create events using the CreateEventByMember choice in the GroupMember template.
8.	Event Organizer (either group owner or member) can invite other group members to events using the InviteToEvent choice in the GroupMemberEvent template.
9.	Invitee can accept event invitations and register for events by providing their consent and creating an EventRegister contract.
10.	Registered users can also cancel their event registrations using the CancelRegistration choice in the EventRegister template.
11.	Event Organizer can cancel events using the CancelEvent choice in the GroupMemberEvent template.
12.   Organizer can mark Event complete successfully.

### III. Challenge(s)
* The project was created by using `empty-skeleton` and the following was removed from `daml.yaml`:
```
sandbox-options:
   - --wall-clock-time
```
and the following was added:

```
exposed-modules:
  - Main
```
For more info, check out [this post](https://discuss.daml.com/t/sandbox-options-wall-clock-time/5692/16?u=cathy_jung) on Daml Forum and [Daml Doc](https://docs.daml.com/tools/navigator/index.html?&_ga=2.48248804.337210607.1673989679-241632404.1672853064&_gac=1.17025355.1673455980.CjwKCAiA2fmdBhBpEiwA4CcHzfI2w1_D95zAr3_d6QTypOMXGTpUxtS06c55inucNwZvUZn4AebsJxoCZEgQAvD_BwE&_gl=1*elem6v*_ga*MjQxNjMyNDA0LjE2NzI4NTMwNjQ.*_ga_GVK9ZHZSMR*MTY3Mzk5NDQzOS4zMS4xLjE2NzM5OTQ3MDcuMC4wLjA.#logging-in-as-a-party).


### IV. Compiling & Testing
To compile and test, run the pre-written script in the `Test.daml` under /daml OR run:
```
$ daml start
```

Test coverage report
```
$ daml test --show-coverage


**Test Summary
**
daml/Main.daml:setupGroupUsers: ok, 0 active contracts, 0 transactions.
daml/Main.daml:setupMemberUsers: ok, 0 active contracts, 0 transactions.
daml/Main.daml:setup: ok, 11 active contracts, 42 transactions.
Modules internal to this package:
- Internal templates
  7 defined
  7 (100.0%) created
  internal templates never created: 0
- Internal template choices
  21 defined
  14 ( 66.7%) exercised
  internal template choices never exercised: 7
    Main:EventInvitation:Archive
    Main:EventRegister:Archive
    Main:Group:Archive
    Main:GroupInvitationRequest:Archive
    Main:GroupMember:Archive
    Main:GroupMemberEvent:Archive
    Main:GroupMemberMessages:Archive
