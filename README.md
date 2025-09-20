
# Button and region Enable / Disable JavaScript code in oracle apex

- Enable / Disable — keeps buttons visible but toggles whether they are clickable (preferred UX in many cases).

# Prerequisites

- Oracle APEX page with the buttons already created.

- Each button should have a Static ID (recommended) or a reliable selector.

- Basic familiarity with APEX page JavaScript regions and apex.jQuery.

## Tip: In APEX, set a Static ID for a button by selecting the button → Advanced → Static ID. Use that ID in selectors #my_button_id.



# Add JavaScript Code (Page load or Item change event):

- Add this javascript code on Page load or Status or Item change event or item change event


```javascript code
function toggleButtons() {
    var status = $v("P38_BILL_STATUS");

    // First disable all buttons
    $("#btn_bill_edit, #approve, #sendToParty, #receiveFromParty, #SubmitToBank, #LdbcIbc, #Maturity, #BankDDFReceive, #Realization")
        .prop("disabled", true);

    // Now enable only the ones allowed for each status
    switch (status) {
        case "INITIALIZE":
            $("#btn_bill_edit, #approve").prop("disabled", false);
            break;

        case "APPROVED":
            $("#sendToParty").prop("disabled", false);
            break;

        case "SEND TO PARTY":
            $("#receiveFromParty").prop("disabled", false);
            break;

        case "RECEIVE FROM PARTY":
            $("#SubmitToBank").prop("disabled", false);
            break;

        case "SUBMIT TO BANK":
            $("#LdbcIbc").prop("disabled", false);
            break;

        case "LDBC IBC":
            $("#Maturity").prop("disabled", false);
            break;

        case "MATURITY":
            $("#BankDDFReceive").prop("disabled", false);
            break;

        case "BANK DDF RECEIVE":
            $("#Realization").prop("disabled", false);
            break;

        default:
            // nothing enabled
            break;
    }
}

// Run after page loads
apex.jQuery(function($){
    toggleButtons();
    // Re-run whenever status changes
    $("#P38_BILL_STATUS").change(toggleButtons);
});


```

 # Thank you
 ## Sanjay Sikder

 You can connect with me on [LinkedIn](https://www.linkedin.com/in/sanjay-sikder/)!
