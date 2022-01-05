

This task should not take you more than 2 hours. Feel free to work on the solution however
you'd like, but please submit it as a single ".jsx" file as an attachment emailed to
ian@streamily.com.

This CustomerDirectory component currently renders a list of 6 customer addresses, each with an
"Edit" button that does nothing.

1. Please add behavior to allow the "Edit" button to open a modal that will allow
the user to edit each of the following customer parameters: first_name, last_name, address, address2,
city, state, and zip_code.

2. The modal should render an input field for each of these parameters, an exit
button to close the modal, and a submit button that will save the new details and display them to
the user in the CustomerDirectory component in place of the old address.

3. All fields, except for
address2, should be required.

4. If the user hits the exit button, none of the customer address details
should be altered in the CustomerDirectory component.

This implementation requires no backend, and can be achieved without the Context API or Redux.
On page refresh, all data will be reset back to the initial values, which is to be expected
when not saving updated details anywhere besides JS. Please use React hooks, such as
useState(), to accomplish this goal. You do not need to import any
packages to achieve this goal, but if you wish to, you may. You will be evaluated upon how
well you implement common development standards and how efficiently and robustly you've
achieved your goal.

Bonus points:
* Save updated customer data to localStorage so that it retains the updated values on page refresh.
* Add the ability to delete a customer
* Add the ability to create a new customer
* The current styling is very basic. Make everything prettier.
* Use a dropdown menu to update the "state" value that allows the user to select a full state name, such
as "California", while setting the React state to the ISO state value counterpart, such as "CA".
* Add the ability to edit the "Country" value to be another country besides "US". Additional bonus points
if you can get the "State" dropdown to change depending upon which country is selected. Populating the
"state" dropdown for even just a few countries would be impressive. Not all countries need to be supported.


```

import React from 'react';

const initCustomerData = [
    {customer_id: 1, first_name: "Bob", last_name: "Smith", address: "87 Main St", address2: "Apt 87", city: "Los Angeles", state: "CA", zip_code: "17435"},
    {customer_id: 2, first_name: "Barb", last_name: "Belmont", address: "84 Palm", address2: null, city: "Petersburg", state: "AR", zip_code: "34625"},
    {customer_id: 3, first_name: "Jerry", last_name: "Seinfeld", address: "4876 22nd", address2: "4", city: "New York City", state: "NY", zip_code: "38756"},
    {customer_id: 4, first_name: "Yijun", last_name: "Li", address: "95 Cherry", address2: null, city: "Orlando", state: "FL", zip_code: "26564"},
    {customer_id: 5, first_name: "Corey", last_name: "Smith", address: "83573 Oregon Ave", address2: "Suite # 544", city: "Eagle Rock", state: "WA", zip_code: "97524"},
    {customer_id: 6, first_name: "Gloria", last_name: "Hernandez", address: "9 Pine Rd", address2: "2", city: "Sacramento", state: "CA", zip_code: "34655"}
];

const Customer = ({data}) => {

    return(
        <div style={{display: 'flex', flexDirection: 'column', alignItems: 'flex-start'}}>
            <div style={{
                padding: '10px', margin: '10px',
                display: 'flex', flexDirection: 'column',
                boxShadow: '1px 1px 2px 1px rgba(0,0,0,0.1)',
                borderRadius: '5px', minWidth: '300px'
            }}>
                <b>Customer Address:</b>
                <div>{data.first_name} {data.last_name}</div>
                <div>{data.address}{data.address2 ? `, ${data.address2}` : ''}</div>
                <div>{data.city}, {data.state}, US {data.zip_code}</div>
                <button style={{margin: '10px', cursor: 'pointer'}}>Edit</button>
            </div>
        </div>
    );
};

const CustomerDirectory = () => {

    return(
        <div>
            <h1 style={{marginLeft: '10px'}}>Customers:</h1>
            <div style={{display: 'flex', flexDirection: 'row', flexWrap: 'wrap'}}>
                {initCustomerData.map(customer=><Customer key={customer.customer_id} data={customer}/>)}
            </div>
        </div>
    );
};

export default CustomerDirectory;

```