# Application-for-Wholesale-Rice-Mill

Creating an Apex Class(ConsumerRecord)
Login to the Salesforce account and navigate to the gear account in the top right corner.
Then we can see the Developer console. Click on the developer console and you will navigate to a new console window.

Then you can see many tools in the Toolbar of the new console window. Click on File, New and Apex Class.
Enter the name of the class(ConsumerRecord) to create a new class file.
Code Snippet : 

class ConsumerRecord {
    public static void sendEmailNotification (List<consumer__c> con){
        for(consumer__c c:con)
        {
            Messaging.SingleEmailMessage email = new Messaging.SingleEmailMessage();
                email.setToAddresses( new List<String>{c.email__c});
                email.setSubject('Welcome to our company');
                email.setPlainTextBody('Dear '  + ' '+ ',\n\nWelcome to MY RICE!'+'You have been seen as a valuable customer to us. PLease continue your journey with us, while we try to provide you with good quality resources.'+'\n'+
                                           "We are proud to associate with valuable customers like you and we look forward to collaborating with you by providing more and more exciting discounts or even product offers too.' + '\n'
                                           +'So why taking a step back, take a leap of faith and shop with us more, while we provide with the valuable products and offers'+'\n'+'\n'+'\n'+
                                           'Thankyou for buying '+ '' +'Here are some of the products that are brought by the customers who similarly bought products like this'+'\n\n');
                Messaging.sendEmail(new List<Messaging.SingleEmailMessage>{email});

        }
    }
}
