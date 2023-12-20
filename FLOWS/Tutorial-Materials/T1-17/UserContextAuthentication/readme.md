Flows to authenticate a user whenever you need to run an API that requires a certain user context.
Examples you will find here:
1. Authenticate with username & password (Identity auth profile has to be setup with single psw factor)

```mermaid
sequenceDiagram
Flows-->>StartAuth:first call (username)
StartAuth-->>Flows:return sessionId and Mechanisms
Flows-->>AdvanceAuth:with sessionId & mechId (ID for Psw)
AdvanceAuth-->>Flows:Token & set-cookies
Flows-->>Identity Endpoints: with cookie = set-cookies
```


2. Authenticate with u/p and a second factor, an OTP by email that needs to be entered in a form.

```mermaid
sequenceDiagram
Flows-->>StartAuth:first call (username)
StartAuth-->>Flows:return sessionId and Mechanisms
Flows-->>AdvanceAuth:with sessionId & mechId (ID for Psw)
AdvanceAuth-->>Flows:ok
Flows-->>FORM: enter OTP
FORM-->>Flows:return OTP
Flows-->>AdvanceAuth2:with sessionId & mechId (ID for Email) & OTP
AdvanceAuth2-->>Flows:token & set-cookies
Flows-->>Identity Endpoints: with cookie = set-cookies
```


3. Authenticate with U/P + Email OTP but click on the short link of the email so that no user interaction is required in the flow.

```mermaid
sequenceDiagram
Flows-->>StartAuth:first call (username)
StartAuth-->>Flows:return sessionId and Mechanisms
Flows-->>AdvanceAuth:with sessionId & mechId (ID for Psw)
AdvanceAuth-->>Flows:ok
Flows-->>AdvanceAuth2:with sessionId & mechId (ID for Email) & StartOOB
Flows-->>AdvanceAuth3: Poll
loop POLLING
    AdvanceAuth3->>AdvanceAuth3: Check if OTP link is clicked
end
AdvanceAuth3-->>Flows:token & set-cookies
AdvanceAuth3-->>Flows:token & set-cookies
Flows-->>Identity Endpoints: with cookie = set-cookies
```
