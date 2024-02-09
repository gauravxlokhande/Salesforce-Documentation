# Access time in js:

<p>The issue is when i accessing time in apex it is in proper format but when i fetching this time into js and accessing in js. when i console it time then it get converted into milisecond so to resolve that issue below code works in js:</p>

![Screenshot 2024-02-09 114155](https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/16d1841a-090d-4fdc-8189-aa78314a90d4)

![Screenshot 2024-02-09 114212](https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/2f3ec70f-e9c7-48cf-9745-acec7aa1b737)

![Screenshot 2024-02-09 114309](https://github.com/gaurravlokhande/Javascript-for-Salesforce-Developers-Lwc-Components-1.md/assets/119065314/fa419d00-c332-424f-92fa-26cc21224487)


```     
    @track storetime;
    

  convertMillisecondsToTime(milliseconds) {
    // Create a new Date object using milliseconds
    const date = new Date(milliseconds);

    // Extract hours, minutes, and seconds
    const hours = date.getUTCHours();
    const minutes = date.getUTCMinutes();
    const seconds = date.getUTCSeconds();

    // Format the time string
    const timeString = hours.toString().padStart(2, '0') + ':' +
                      minutes.toString().padStart(2, '0') + ':' +
                      seconds.toString().padStart(2, '0');

    return timeString;
}

    connectedCallback() {
        this.handleDataReceived(37800000);
    }
    
// Example usage:
handleDataReceived(milliseconds) {
    const formattedTime = this.convertMillisecondsToTime(milliseconds);
    console.log(formattedTime); // Output to console
    // Further processing or UI updates can be done here
}

```
