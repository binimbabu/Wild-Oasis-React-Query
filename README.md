<--------------------------------------Code not working for reference only ----------------------------------------------------------->





Project WildOasis requirement 

1. Authentication
Users of the app are hotel emplyees. They need to be logged into the application to perform tasks.
New users can only be signed up insde the applications ( to guarantee that only actual hotel employees can get accounts)
Users should be able to upload an avatar, and change their name and password.

2.Cabins
App needs a table view with all cabins, showing the cabin photo, name, capacity, price and current discount
Users should be able to update or delete a cabin and to create new cabins (including uploading a photo)

3. Bookings
App needs a table view with all bookings showing arrival and departure dates status and paid amount as well as cabin and guest data.
The booking status can be "unconfirmed" (booked but not yet checked in), "checked in" or "checked out". The table should be filterable by this important status.
Other booking data includes : number of guests, number of nights, guest observations, whether they booked breakfast , breakfast price.

4. Check in /out
Users should be able to delete, check in or check out a booking as the guest arrives (no editing necessary for now)
Bookings may not have been paid yet on guest arrival. Therefore on check in users need to accept payment (outside the app) and then confirm the payment has been received (inside the app).
On check in the guest should have the ability to add breakfast for the entire stay if they hadn't already

5. Guests
Guest data should contain : full name , email, national ID, nationality and a country flag for easy identification.

6. Dashboard
The initial app screen should be a dashboard to display important information for thelast 7, 30 or 90 days: 
  A list of guests checking in and out on the current day. Users should be able to perform these tasks from here 
  Statistics on recent bookings, sales, check ins, and occupancy rate
  A chart showing all daily hotel sales, showing both "total" sales and "extras" sales (only breakfast at the moment)
  A chart showing statistics on stay durations as this is an important metric for the hotel.

7. Settings
Users should be able to define a few application wide settings: breakfast price min and max nights/booking, max guests/booking

App need a dark mode


Features + pages

Feature categories
1. Bookings
2. Cabins
3. Guests
4. Dashboard
5. Check in and out
6. App settings
7. Authentication

Necessary pages
1. Dashboard (/dashboard)
2. Bookings  (/bookings)
3. Cabins (/cabins)
4. Booking check in (/checkin/:bookingID)
5. App settings (/settings)
6. User sign up (/users)
7. Login (/login)
8. Account stings (/account)


Client side rendering and server side rendering

1. Client side rendering with plain React

Used to build single page applications.
All HTML is rendered on the client.
Rendering of Client side rendering which means JavaScript needs to be downloaded before apps start running (bad for performance when using low internet).
One perfect use case: apps that are used "internally" as tools inside companies that are entirely hidden behind a login.

2. Server side rendering with framework like Next.js

Used to build Multi page applications.
Soe HTML i rendered in the server.
More performant as less JavaScript needs to be downloaded.







For routing in WildOasis project we use React Router.
For styling in WildOasis project we use styled components.
Remote state management used in WildOasis project is React Query (best way of managing remote state with features like caching, automatic re-fetching, pre-fetching, offline support etc.
UI state management in WildOasis project used here is context API ( there is almost no UI state needed in this app, so simple context with useState will be enough no need for redux).
Form management used in WildOasis is React Hook Form (handling bigger forms can be a lot of work as manual state creation and errorhandling, alibrary can simplify all this)
React hot toast for notifications, recharts for displaying beautiful charts, date-fns for date manipulation.


npm create vite@4

Also do 'npm install'

To install styled components the following command:-

npm install styled-components






Import styled-components in the react components


App.jsx

import styled from "styled-components";
import GlobalStyles from "./styles/GlobalStyles";

const H1 = styled.h1`
font-size: 30px;
font-weight: 600;
`
const Button = styled.button`
  font-size: 1.4rem;
  padding: 1.2rem 1.6rem;
  font-weight: 500;
  border: none;
  background-color: purple;
  color: white;
  margin: 20px;
  cursor: pointer;
`

const Input = styled.input`
  border: 1px solid #ddd;
  border-radius: 5px;
  padding: 0.8rem 1.2rem;
`

const StyledApp = styled.div`
background-color: orangered;
padding: 20px;
`

function App() {
  return (
    <>
     <GlobalStyles />
     <StyledApp>
      <H1>Hello World</H1>
      <Button onClick={()=>alert("Check in")}>Check in</Button>
      <Button onClick={()=>alert("Check out")}>Check out</Button>
      <Input type="number" placeholder="Number of Guests" />
     </StyledApp>
    </>
  )
}

export default App




Install VS code extensions 'vscode-styled-components'



Global styles with styled components


styles/GlobalStyles.js



import { createGlobalStyle } from "styled-components";

const GlobalStyles = createGlobalStyle`
:root {
  /* Indigo */
  --color-brand-50: #eef2ff;
  --color-brand-100: #e0e7ff;
  --color-brand-200: #c7d2fe;
  --color-brand-500: #6366f1;
  --color-brand-600: #4f46e5;
  --color-brand-700: #4338ca;
  --color-brand-800: #3730a3;
  --color-brand-900: #312e81;

  /* Grey */
  --color-grey-0: #fff;
  --color-grey-50: #f9fafb;
  --color-grey-100: #f3f4f6;
  --color-grey-200: #e5e7eb;
  --color-grey-300: #d1d5db;
  --color-grey-400: #9ca3af;
  --color-grey-500: #6b7280;
  --color-grey-600: #4b5563;
  --color-grey-700: #374151;
  --color-grey-800: #1f2937;
  --color-grey-900: #111827;

  --color-blue-100: #e0f2fe;
  --color-blue-700: #0369a1;
  --color-green-100: #dcfce7;
  --color-green-700: #15803d;
  --color-yellow-100: #fef9c3;
  --color-yellow-700: #a16207;
  --color-silver-100: #e5e7eb;
  --color-silver-700: #374151;
  --color-indigo-100: #e0e7ff;
  --color-indigo-700: #4338ca;

  --color-red-100: #fee2e2;
  --color-red-700: #b91c1c;
  --color-red-800: #991b1b;

  --backdrop-color: rgba(255, 255, 255, 0.1);

  --shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.04);
  --shadow-md: 0px 0.6rem 2.4rem rgba(0, 0, 0, 0.06);
  --shadow-lg: 0 2.4rem 3.2rem rgba(0, 0, 0, 0.12);

  --border-radius-tiny: 3px;
  --border-radius-sm: 5px;
  --border-radius-md: 7px;
  --border-radius-lg: 9px;

  /* For dark mode */
  --image-grayscale: 0;
  --image-opacity: 100%;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  padding: 0;
  margin: 0;

  /* Creating animations for dark mode */
  transition: background-color 0.3s, border 0.3s;
}

html {
  font-size: 62.5%;
}

body {
  font-family: "Poppins", sans-serif;
  color: var(--color-grey-700);

  transition: color 0.3s, background-color 0.3s;
  min-height: 100vh;
  line-height: 1.5;
  font-size: 1.6rem;
}

input,
button,
textarea,
select {
  font: inherit;
  color: inherit;
}

button {
  cursor: pointer;
}

*:disabled {
  cursor: not-allowed;
}

select:disabled,
input:disabled {
  background-color: var(--color-grey-200);
  color: var(--color-grey-500);
}

input:focus,
button:focus,
textarea:focus,
select:focus {
  outline: 2px solid var(--color-brand-600);
  outline-offset: -1px;
}

/* Parent selector, finally 😃 */
button:has(svg) {
  line-height: 0;
}

a {
  color: inherit;
  text-decoration: none;
}

ul {
  list-style: none;
}

p,
h1,
h2,
h3,
h4,
h5,
h6 {
  overflow-wrap: break-word;
  hyphens: auto;
}

img {
  max-width: 100%;

  /* For dark mode */
  filter: grayscale(var(--image-grayscale)) opacity(var(--image-opacity));
}
`


export default GlobalStyles;



App.jsx


import styled from "styled-components";
import GlobalStyles from "./styles/GlobalStyles";
import Button from "./ui/Button";
import Input from "./ui/Input";

const H1 = styled.h1`
font-size: 30px;
font-weight: 600;
`

const StyledApp = styled.div`
background-color: orangered;
padding: 20px;
`

function App() {
  return (
    <>
     <GlobalStyles />
     <StyledApp>
      <H1>Hello World</H1>
      <Button onClick={()=>alert("Check in")}>Check in</Button>
      <Button onClick={()=>alert("Check out")}>Check out</Button>
      <Input type="number" placeholder="Number of Guests" />
     </StyledApp>
    </>
  )
}

export default App





Input.jsx



import styled from "styled-components";
const Input = styled.input`
  border: 1px solid var(--color-grey-300);
  background-color: var(--color-grey-0);
  border-radius:  var(--border-radius-sm);
  padding: 0.8rem 1.2rem;
  box-shadow: var(--shadow-sm);
`

export default Input;



Button.jsx


import styled, { css } from "styled-components";

const sizes = {
  small: css`
    font-size: 1.2rem;
    padding: 0.4rem 0.8rem;
    text-transform: uppercase;
    font-weight: 600;
    text-align: center;
  `,
  medium: css`
    font-size: 1.4rem;
    padding: 1.2rem 1.6rem;
    font-weight: 500;
  `,
  large: css`
    font-size: 1.6rem;
    padding: 1.2rem 2.4rem;
    font-weight: 500;
  `,
};

const variations = {
  primary: css`
    color: var(--color-brand-50);
    background-color: var(--color-brand-600);

    &:hover {
      background-color: var(--color-brand-700);
    }
  `,
  secondary: css`
    color: var(--color-grey-600);
    background: var(--color-grey-0);
    border: 1px solid var(--color-grey-200);

    &:hover {
      background-color: var(--color-grey-50);
    }
  `,
  danger: css`
    color: var(--color-red-100);
    background-color: var(--color-red-700);

    &:hover {
      background-color: var(--color-red-800);
    }
  `,
};

const Button = styled.button`
  font-size: 1.4rem;
  padding: 1.2rem 1.6rem;
  font-weight: 500;
  border: var(--border-radius-sm);
  background-color: var(--color-brand-500);
  color: var(--color-brand-50);
  box-shadow: var(--shadow-sm);
  cursor: pointer;

  &:hover {
      background-color: var(--color-brand-700);
    }
`
export default Button;






To add a variable for css we can add the following, where 'css' is a helper function to generate CSS from a template literal with interpolations.

const test = css`
    text-align: center;
`



Full code Heading.jsx


import styled, { css } from "styled-components";

const test = css`
    text-align: center;
`

const Heading = styled.h1`
font-size: 30px;
font-weight: 600;
${test}
`

export default Heading;




Passing prop to 'Heading' component


We can pass 'type' to Heading component from App.jsx like below and 'as' property ensures we refer to 'h2' or 'h3' in the HTML tag. Whatever we pass to 'as' property will be the lement to be rendered in HTML.


<Heading as="h1">Hello World</Heading>
<Heading as="h2">Check in and out</Heading>
<Heading as="h3">Form</Heading>



Full App.jsx



import styled from "styled-components";
import GlobalStyles from "./styles/GlobalStyles";
import Button from "./ui/Button";
import Input from "./ui/Input";
import Heading from './ui/Heading'
const StyledApp = styled.div`
background-color: orangered;
padding: 20px;
`

function App() {
  return (
    <>
     <GlobalStyles />
     <StyledApp>
      <Heading as="h1">Hello World</Heading>
      <Heading as="h2">Check in and out</Heading>
      <Button onClick={()=>alert("Check in")}>Check in</Button>
      <Button onClick={()=>alert("Check out")}>Check out</Button>
      <Heading as="h3">Form</Heading>
      <Input type="number" placeholder="Number of Guests" />
     </StyledApp>
    </>
  )
}

export default App


Heading.jsx


import styled, { css } from "styled-components";



const Heading = styled.h1`
${(props) => props.as === 'h1' && css`
    font-size: 30px;
    font-weight: 600;
`}
line-height: 1.4
`

export default Heading;



Here the following code snippet from above the code 

${(props) => props.as === 'h1' && css`
    font-size: 30px;
    font-weight: 600;
`}

Here we are accepting 'props' from App.jsx in Heading.jsx checking if 'as = h1' then css is set to the  'font-size: 30px; font-weight: 600; '. Similarly for 'type = h2' and 'type = h3'





Full code Heading.jsx



import styled, { css } from "styled-components";



const Heading = styled.h1`
${(props) => props.as === 'h1' && css`
    font-size: 3rem;
    font-weight: 600;
`}
${(props) => props.as === 'h2' && css`
    font-size: 2rem;
    font-weight: 600; 
`}
${(props) => props.as === 'h3' && css`
    font-size: 1rem;
    font-weight: 500;
`}
line-height: 1.4
`

export default Heading;





Reusable styled components

In App.jsx we use 'variant' and 'size' in 'Button' component

<Button variation="primary" size="medium" onClick={()=>alert("Check in")}>Check in</Button>
<Button variation="secondary" size="small" onClick={()=>alert("Check out")}>Check out</Button>



In 'Button.jsx' 


const Button = styled.button`
  border: none;
  border-radius: var(--border-radius-sm);
  box-shadow: var(--shadow-sm);
  ${(props => sizes[props.size])}
  ${(props=> variations[props.variation])}
`


Button.defaultProps = {
  variation :  'primary',
  size: 'medium'
}



'defaultProps' is to set default props. So 'Check in' button will have this default props.




Full App.jsx


import styled from "styled-components";
import GlobalStyles from "./styles/GlobalStyles";
import Button from "./ui/Button";
import Input from "./ui/Input";
import Heading from './ui/Heading'
import Row from "./ui/Row";
const StyledApp = styled.div`
padding: 20px;
`

function App() {
  return (
    <>
     <GlobalStyles />
     <StyledApp>
      <Row type="vertical">
       <Row type="horizontal">
      <Heading as="h1">Hello World</Heading>
      <div>
      <Heading as="h2">Check in and out</Heading>
      <Button onClick={()=>alert("Check in")}>Check in</Button>
      <Button variation="secondary" size="small" onClick={()=>alert("Check out")}>Check out</Button>
      </div>
     
      </Row>
      <Row type="vertical">
       <Heading as="h3">Form</Heading>
      <form>
        <Input type="number" placeholder="Number of Guests" />
      </form>
      </Row>
      </Row>
     </StyledApp>
    </>
  )
}

export default App




Full Button.jsx


import styled, { css } from "styled-components";

const sizes = {
  small: css`
    font-size: 1.2rem;
    padding: 0.4rem 0.8rem;
    text-transform: uppercase;
    font-weight: 600;
    text-align: center;
  `,
  medium: css`
    font-size: 1.4rem;
    padding: 1.2rem 1.6rem;
    font-weight: 500;
  `,
  large: css`
    font-size: 1.6rem;
    padding: 1.2rem 2.4rem;
    font-weight: 500;
  `,
};

const variations = {
  primary: css`
    color: var(--color-brand-50);
    background-color: var(--color-brand-600);

    &:hover {
      background-color: var(--color-brand-700);
    }
  `,
  secondary: css`
    color: var(--color-grey-600);
    background: var(--color-grey-0);
    border: 1px solid var(--color-grey-200);

    &:hover {
      background-color: var(--color-grey-50);
    }
  `,
  danger: css`
    color: var(--color-red-100);
    background-color: var(--color-red-700);

    &:hover {
      background-color: var(--color-red-800);
    }
  `,
};

const Button = styled.button`
  border: none;
  border-radius: var(--border-radius-sm);
  box-shadow: var(--shadow-sm);
  ${(props => sizes[props.size])}
  ${(props=> variations[props.variation])}
`

Button.defaultProps = {
  variation :  'primary',
  size: 'medium'
}
export default Button;




Install react router

npm i react-router-dom@6




App.jsx modified to he following


import styled from "styled-components";
import GlobalStyles from "./styles/GlobalStyles";
import AppLayout from './ui/AppLayout'
import { BrowserRouter, Routes, Route, Navigate } from "react-router-dom";
import Dashboard from './pages/Dashboard'
import Bookings from './pages/Bookings';
import Cabins from './pages/Cabins';
import Users from './pages/Users';
import Settings from './pages/Settings';
import Account from './pages/Account';
import Login from './pages/Login';
import PageNotFound from './pages/PageNotFound';



function App() {
  return (
    <>
    <GlobalStyles />
    <BrowserRouter>
    <Routes>
      <Route element={<AppLayout />}>
      <Route index element={<Navigate replace to="dashboard" />} />
      <Route path="dashboard" element={<Dashboard />} />
      <Route path="bookings" element={<Bookings />} />
      <Route path="cabins" element={<Cabins />} />
      <Route path="users" element={<Users />} />
      <Route path="settings" element={<Settings />} />
      <Route path="account" element={<Account />} />
      </Route>
      <Route path="login" element={<Login />} />
      <Route path="*" element={<PageNotFound />} />
    </Routes>
    </BrowserRouter>
    </>
    
  )
}

export default App


Here 'AppLayout.jsx' is placed inside src/ui folder and components like 'Dashboard', 'Bookings', 'Cabins', 'Users', 'Settings', 'Account' are child routes to the 'AppLayout' route. And give <Outlet /> in AppLayout.jsx



AppLayout.jsx


import { Outlet } from "react-router-dom";

export default function AppLayout(){
    return (
        <div>
            <h1>App Layout</h1>
            <Outlet />
        </div>
    )
}






create 2 files 'Header.jsx' and 'Sidebar.jsx' in 'ui' folder.



AppLayout.jx


import { Outlet } from "react-router-dom";
import Header from "./Header";
import Sidebar from "./Sidebar";
import styled from "styled-components";

const StyledAppLayout = styled.div`
    display: grid;
    grid-template-columns: 26rem 1fr;
    grid-template-rows: auto 1fr;
    height: 100vh;
`

const Main = styled.main`
    background-color: var(--color-grey-50);
    padding: 4rem 4.8rem 6.4rem;
`

export default function AppLayout(){
    return (
        <StyledAppLayout>
            <Header />
            <Sidebar />
            <Main>
             <Outlet />
            </Main>
        </StyledAppLayout>
    )
}




Header.jsx


import styled from "styled-components"

const StyledHeader = styled.header`
    background-color: var(--color-grey-0);
    padding: 1.2rem 4.8rem;
    border-radius: 1px solid var(--color-grey-100);
`


export default function Header(){
    return (
        <StyledHeader>
        header
        </StyledHeader>
    )
}



Sidebar.jsx


import styled from "styled-components"

const StyledSidebar = styled.aside`
    background-color: var(--color-grey-0);
    padding: 3.2rem 2.4rem;
    border-right: 1px solid var(--color-grey-100);
    grid-row: 1 / -1;
    display: flex;
    flex-direction: column;
    gap: 3.2rem;
`

export default function Sidebar(){
    return (
        <StyledSidebar>
        <Logo />
        <MainNav />
        </StyledSidebar>
     
    )
}



Install react icons

npm i react-icons



MainNav.jsx


import { NavLink } from "react-router-dom";
import styled from "styled-components";
import { HiOutlineCalendarDays, HiOutlineCog6Tooth, HiOutlineHome, HiOutlineHomeModern } from "react-icons/hi2"
import { HiOutlineUser } from "react-icons/hi";

const NavList = styled.ul`
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
`;

const StyledNavLink = styled(NavLink)`
  &:link,
  &:visited {
    display: flex;
    align-items: center;
    gap: 1.2rem;

    color: var(--color-grey-600);
    font-size: 1.6rem;
    font-weight: 500;
    padding: 1.2rem 2.4rem;
    transition: all 0.3s;
  }

  /* This works because react-router places the active class on the active NavLink */
  &:hover,
  &:active,
  &.active:link,
  &.active:visited {
    color: var(--color-grey-800);
    background-color: var(--color-grey-50);
    border-radius: var(--border-radius-sm);
  }

  & svg {
    width: 2.4rem;
    height: 2.4rem;
    color: var(--color-grey-400);
    transition: all 0.3s;
  }

  &:hover svg,
  &:active svg,
  &.active:link svg,
  &.active:visited svg {
    color: var(--color-brand-600);
  }
`;


export default function MainNav(){
  return (
    <nav>
    <NavList>
      <li>
        <StyledNavLink to="/dashboard"><HiOutlineHome /><span>Home</span></StyledNavLink>
      </li>
      <li>
        <StyledNavLink to="/bookings"><HiOutlineCalendarDays /><span>Bookings</span> </StyledNavLink>
      </li>
       <li>
        <StyledNavLink to="/cabins"><HiOutlineHomeModern /><span>Cabins</span> </StyledNavLink>
      </li>
      <li>
        <StyledNavLink to="/users"><HiOutlineUser /><span>Users</span> </StyledNavLink>
      </li>
       <li>
        <StyledNavLink to="/settings"><HiOutlineCog6Tooth /><span>Settings</span> </StyledNavLink>
      </li>
    </NavList>
    </nav>
)
}













React Query

React query manages remote state (state saved in server and need to load the application. React query is a data fetching library. All remote state in React query is cached which eans fetched data will be stored inorder to be reused in different points of the application. 
For example if we fetch data about cabin A in component A, react query will fetch data from API, then will store the received data in cache so component A can use it. But if component B want to fetch cabin data then no additional API request will be necessary, that is react query will given the same data to component B from cache. The advantage of React Query is it wastes a bit less data to be downloaded, once data in the cache all other components like component B can receive it instantly (without showing spinner this leads to fast experience for users). React query gives all loading and error states. React query automatically re fetches to keep state synched in certain situations like after certain timeout, after leave browser window and then come back to it (this ensures remote state always remains synched with the application). For example other component updates the cabin data then application running on all other computers will have cabin state synched with the newly updated state. Pre-fetching to fetch data that is necessary later but before actually displayed on the screen (example of pre-fetching is pagination where data in current page as well as next page is made available as it is available in the cache).

npm i @tanstack/react-query@4

React query first step is to place data basically lives, second provide to the application. 
In App.js

import { QueryClient } from "@tanstack/react-query";
import { ReactQueryDevtools } from "@tanstack/react-query-devtools";
const queryClient = new  QueryClient(
{
defaultOptions: {
 queries : {
staleTime: 60 *1000
  }
}
});

export default function App(){
return (
 <QueryClientProvider client={queryClient}>
 <ReactQueryDevtools initialIsOpen= {false} />
  <Header/>
  <Main />
  <Footer />
 </QueryClientProvider>
)
}


'staleTime' is the amount of time that data in the cache will stay fresh so that it will stay valid until re-fetched again. 'staleTime: 60 *1000' here 60 denotes seconds and 1000 milliseconds. Then 'QueryClientProvider' component on as the parent tag in 'App.js' and provide with 'client'.
React query has dev tools which can be installed by the following command :-

npm i @tanstack/react-query-devtools



If you want to use React Query v5, there are only two small things to change in the project:

isLoading is now called isPending

The cacheTime option is now called gcTime



React Query - useQuery

In React Querywe use 'useQuery' custom hook. In 'useQuery' we pass an object (in the object we pass 2 arguments, first argument is 'queryKey' (to uniquely identify the query here, the value in 'queryKey' is a complex array or an array with strings, here in the below example 'cabin' is to uniquely identifies each data (when we use 'useQuery' in another page with same 'queryKey' say 'cabin' then data will be read from the cache ) ) and second argument is the query function 'queryFn' ( query function is responsible for querying, basically fetching data from API ) 

import getCabins from '../../services/apiCabins'; //api not created for fetching data


const { isLoading, data: cabins, error} = useQuery({
  queryKey : ["cabin"],
  queryFn: getCabins
})


CabinTable.jsx



import { useQuery } from "@tanstack/react-query";
import styled from "styled-components";
import getCabins from '../../services/apiCabins'; //api not created for fetching data
import Spinner from '../../ui/Spinner';
import CabinRow from "./CabinRow";


const Table = styled.div`
  border: 1px solid var(--color-grey-200);

  font-size: 1.4rem;
  background-color: var(--color-grey-0);
  border-radius: 7px;
  overflow: hidden;
`;

const TableHeader = styled.header`
  display: grid;
  grid-template-columns: 0.6fr 1.8fr 2.2fr 1fr 1fr 1fr;
  column-gap: 2.4rem;
  align-items: center;

  background-color: var(--color-grey-50);
  border-bottom: 1px solid var(--color-grey-100);
  text-transform: uppercase;
  letter-spacing: 0.4px;
  font-weight: 600;
  color: var(--color-grey-600);
  padding: 1.6rem 2.4rem;
`;

export default function CabinTable(){
const { isLoading, data: cabins, error} = useQuery({
  queryKey : ["cabin"],
  queryFn: getCabins
})

if(isLoading) return <Spinner />

  return(
  <Table role="table">
    <TableHeader role="row">
      <div></div>
      <div>Cabin</div>
      <div>Capacity</div>
      <div>Price</div>
      <div>Discount</div>
    </TableHeader>
    {cabins.map(cabin => <CabinRow cabin={cabin} key={cabin.id} />)}
  </Table>
  )
}






npm i date-fns

this is to install date functions.


CabinRow.jsx


import styled from "styled-components";
import {formatCurrency} from "../../utils/helpers"


const TableRow = styled.div`
  display: grid;
  grid-template-columns: 0.6fr 1.8fr 2.2fr 1fr 1fr 1fr;
  column-gap: 2.4rem;
  align-items: center;
  padding: 1.4rem 2.4rem;

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }
`;

const Img = styled.img`
  display: block;
  width: 6.4rem;
  aspect-ratio: 3 / 2;
  object-fit: cover;
  object-position: center;
  transform: scale(1.5) translateX(-7px);
`;

const Cabin = styled.div`
  font-size: 1.6rem;
  font-weight: 600;
  color: var(--color-grey-600);
  font-family: "Sono";
`;

const Price = styled.div`
  font-family: "Sono";
  font-weight: 600;
`;

const Discount = styled.div`
  font-family: "Sono";
  font-weight: 500;
  color: var(--color-green-700);
`;

export default function CabinRow({cabin}){
const {id, name, maxCapacity, regularPrice, discount, image} = cabin;

  return (
    <TableRow role="row">
     <Img src="image" />
     <Cabin>{name}</Cabin>
     <div>
      Fits upto {maxCapacity} guests
     </div>
     <Price>{formatCurrency(regularPrice)}</Price>
     <Discount>{formatCurrency(discount)}</Discount>
     <button>Delete</button>
    </TableRow>
  )
}


If we go to another page where other than API data is fetched and displayed move away from this component which will be then unmounted. So, the 'querKey' which is 'cabin' where cabin data is inactive and again the Api data displayed need not have to fetch new fetch request. So, the same data again without any new fetch request hence even the spinner comes since we have the data from before as the data comes from stored cache. 
When we move away from the browser and come back later that will trigger a re-fetch as soon as data is stale.
When some user of the application changes something and so all the applications running on other browsers will come out of sync, so React Query will prevent from automatically re fetching the data.
When we change data within stale time completes then the React Query doesn't fetches it waits until data is stale. But if 'staleTime' (provided in App.jsx) is exceeded then refecthing of data happens as data was changed.




Mutations using React Query 


Deleting a cabin 

Mutation can be done using 'useMutation', in 'useMutation' we pass an object, the first argument in 'useMutation' is 'mutationFn' ('mutationFn' is the function that React Query will call ), second argument is 'onSuccess' (callback which tell React Query what to do as soon as mutation was successful). 'queryClient' in App.jsx can be accessible by a hook 'useQueryClient'


useMutation is used for actions that modify data, such as:

Creating data (POST)

Updating data (PUT / PATCH)

Deleting data (DELETE)

Submitting forms

Triggering side-effect operations (e.g., sending emails, payments)



queryClient.invalidateQueries({ queryKey: ['todos'] })
An invalidated query:

Is marked as stale

Will refetch the next time it’s used (or immediately if active)

Keeps its cached data until the refetch completes


const { isLoading : isDeleting, mutate } = useMutation({
  mutationFn: (id) => deleteCabin(id), onSuccess: () =>{
    queryClient.invalidateQueries({
      queryKey: ["cabin"],

    })
  },
  onError: err => alert(err.message)
})




CabinRow.jsx


import styled from "styled-components";
import {formatCurrency} from "../../utils/helpers"
import { useMutation, useQueryClient } from "@tanstack/react-query";
import deleteCabin from '../../services/apiCabins'

const TableRow = styled.div`
  display: grid;
  grid-template-columns: 0.6fr 1.8fr 2.2fr 1fr 1fr 1fr;
  column-gap: 2.4rem;
  align-items: center;
  padding: 1.4rem 2.4rem;

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }
`;

const Img = styled.img`
  display: block;
  width: 6.4rem;
  aspect-ratio: 3 / 2;
  object-fit: cover;
  object-position: center;
  transform: scale(1.5) translateX(-7px);
`;

const Cabin = styled.div`
  font-size: 1.6rem;
  font-weight: 600;
  color: var(--color-grey-600);
  font-family: "Sono";
`;

const Price = styled.div`
  font-family: "Sono";
  font-weight: 600;
`;

const Discount = styled.div`
  font-family: "Sono";
  font-weight: 500;
  color: var(--color-green-700);
`;

export default function CabinRow({cabin}){
const {id: cabinId, name, maxCapacity, regularPrice, discount, image} = cabin;

const queryClient = useQueryClient();

const { isLoading : isDeleting, mutate } = useMutation({
  mutationFn: (id) => deleteCabin(id), onSuccess: () =>{
    queryClient.invalidateQueries({
      queryKey: ["cabin"],

    })
  },
  onError: err => alert(err.message)
})


  return (
    <TableRow role="row">
     <Img src="image" />
     <Cabin>{name}</Cabin>
     <div>
      Fits upto {maxCapacity} guests
     </div>
     <Price>{formatCurrency(regularPrice)}</Price>
     <Discount>{formatCurrency(discount)}</Discount>
     <button onClick={()=> mutate(cabinId)} disabled={isDeleting}>Delete</button>
    </TableRow>
  )
}



In CabinRow.jsx we add mutate() function in 'Delete' button.


const {id: cabinId, name, maxCapacity, regularPrice, discount, image} = cabin;
 <button onClick={()=> mutate(cabinId)} disabled={isLoading}>Delete</button>


The 'mutate()' will call 'mutationFn' which will indeed call 'deleteCabin(id)'.





Toast Notifications

npm i react-hot-toast

component is called '<Toaster>'


<Toaster position="top-center" gutter={12} />

'gutter' space between the window and toaster. Position at top center.
'containerStyle' specify an object of styles. In 'toastOptions' we have 'success' property with 'duration' to how long success toast will stay in the screen. 



    <Toaster position="top-center" gutter={12} containerStyle={{margin: "8px"}} toastOptions={{success: {
      duration: 3000
    },
    error: {
      duration: 5000
    },
    style:{
      fontSize: '16px',
      maxWidth: '500px',
      padding: '16px 24px',
      backgroundColor: "var(--color-grey-0)",
      color: "var(--color-grey-700)"
    }
    }}/>




App.jsx


import styled from "styled-components";
import GlobalStyles from "./styles/GlobalStyles";
import AppLayout from './ui/AppLayout'
import { BrowserRouter, Routes, Route, Navigate } from "react-router-dom";
import Dashboard from './pages/Dashboard'
import Bookings from './pages/Bookings';
import Cabins from './pages/Cabins';
import Users from './pages/Users';
import Settings from './pages/Settings';
import Account from './pages/Account';
import Login from './pages/Login';
import PageNotFound from './pages/PageNotFound';
import { QueryClient } from "@tanstack/react-query";
import { Toaster } from "react-hot-toast";

const queryClient = new  QueryClient(
{
defaultOptions: {
 queries : {
staleTime: 60 *1000
  }
}
});

function App() {
  return (
    <>
    <QueryClientProvider client={queryClient}>
    <GlobalStyles />
    <BrowserRouter>
    <Routes>
      <Route element={<AppLayout />}>
      <Route index element={<Navigate replace to="dashboard" />} />
      <Route path="dashboard" element={<Dashboard />} />
      <Route path="bookings" element={<Bookings />} />
      <Route path="cabins" element={<Cabins />} />
      <Route path="users" element={<Users />} />
      <Route path="settings" element={<Settings />} />
      <Route path="account" element={<Account />} />
      </Route>
      <Route path="login" element={<Login />} />
      <Route path="*" element={<PageNotFound />} />
    </Routes>
    </BrowserRouter>
    <Toaster position="top-center" gutter={12} containerStyle={{margin: "8px"}} toastOptions={{success: {
      duration: 3000
    },
    error: {
      duration: 5000
    },
    style:{
      fontSize: '16px',
      maxWidth: '500px',
      padding: '16px 24px',
      backgroundColor: "var(--color-grey-0)",
      color: "var(--color-grey-700)"
    }
    }}/>
    </QueryClientProvider>
    </>
    
  )
}

export default App



CabinRow.jsx


import styled from "styled-components";
import {formatCurrency} from "../../utils/helpers"
import { useMutation, useQueryClient } from "@tanstack/react-query";
import deleteCabin from '../../services/apiCabins'
import toast from "react-hot-toast";

const TableRow = styled.div`
  display: grid;
  grid-template-columns: 0.6fr 1.8fr 2.2fr 1fr 1fr 1fr;
  column-gap: 2.4rem;
  align-items: center;
  padding: 1.4rem 2.4rem;

  &:not(:last-child) {
    border-bottom: 1px solid var(--color-grey-100);
  }
`;

const Img = styled.img`
  display: block;
  width: 6.4rem;
  aspect-ratio: 3 / 2;
  object-fit: cover;
  object-position: center;
  transform: scale(1.5) translateX(-7px);
`;

const Cabin = styled.div`
  font-size: 1.6rem;
  font-weight: 600;
  color: var(--color-grey-600);
  font-family: "Sono";
`;

const Price = styled.div`
  font-family: "Sono";
  font-weight: 600;
`;

const Discount = styled.div`
  font-family: "Sono";
  font-weight: 500;
  color: var(--color-green-700);
`;

export default function CabinRow({cabin}){
const {id: cabinId, name, maxCapacity, regularPrice, discount, image} = cabin;

const queryClient = useQueryClient();

const { isLoading : isDeleting, mutate } = useMutation({
  mutationFn: (id) => deleteCabin(id), onSuccess: () =>{
    toast.success("cabins successfully deleted")
    queryClient.invalidateQueries({
      queryKey: ["cabin"],

    })
  },
  onError: err => toast.error(err.message)
})


  return (
    <TableRow role="row">
     <Img src="image" />
     <Cabin>{name}</Cabin>
     <div>
      Fits upto {maxCapacity} guests
     </div>
     <Price>{formatCurrency(regularPrice)}</Price>
     <Discount>{formatCurrency(discount)}</Discount>
     <button onClick={()=> mutate(cabinId)} disabled={isDeleting}>Delete</button>
    </TableRow>
  )
}





CabinTable.jsx


import { useQuery } from "@tanstack/react-query";
import styled from "styled-components";
import getCabins from '../../services/apiCabins'; //api not created for fetching data
import Spinner from '../../ui/Spinner';
import CabinRow from "./CabinRow";


const Table = styled.div`
  border: 1px solid var(--color-grey-200);

  font-size: 1.4rem;
  background-color: var(--color-grey-0);
  border-radius: 7px;
  overflow: hidden;
`;

const TableHeader = styled.header`
  display: grid;
  grid-template-columns: 0.6fr 1.8fr 2.2fr 1fr 1fr 1fr;
  column-gap: 2.4rem;
  align-items: center;

  background-color: var(--color-grey-50);
  border-bottom: 1px solid var(--color-grey-100);
  text-transform: uppercase;
  letter-spacing: 0.4px;
  font-weight: 600;
  color: var(--color-grey-600);
  padding: 1.6rem 2.4rem;
`;

export default function CabinTable(){
const { isLoading, data: cabins, error} = useQuery({
  queryKey : ["cabin"],
  queryFn: getCabins
})

if(isLoading) return <Spinner />

  return(
  <Table role="table">
    <TableHeader role="row">
      <div></div>
      <div>Cabin</div>
      <div>Capacity</div>
      <div>Price</div>
      <div>Discount</div>
    </TableHeader>
    {cabins.map(cabin => <CabinRow cabin={cabin} key={cabin.id} />)}
  </Table>
  )
}



AppLayout.jsx


import { Outlet } from "react-router-dom";
import Header from "./Header";
import Sidebar from "./Sidebar";
import styled from "styled-components";
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';

const queryClient = new  QueryClient(
{
defaultOptions: {
 queries : {
staleTime: 60 *1000
  }
}
});
const StyledAppLayout = styled.div`
    display: grid;
    grid-template-columns: 26rem 1fr;
    grid-template-rows: auto 1fr;
    height: 100vh;
`

const Main = styled.main`
    background-color: var(--color-grey-50);
    padding: 4rem 4.8rem 6.4rem;
`

const Container = styled.div`
  max-width: 120rem;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 3.2rem;
`

export default function AppLayout(){
    return (
        <QueryClientProvider client={queryClient}>
          <StyledAppLayout>
            <Header />
            <Sidebar />
            <Main>
              <Container>
                <Outlet />
              </Container>
            </Main>
        </StyledAppLayout>
         </QueryClientProvider>
    )
}





React Hook Form

React Hook Form handles form submission and form errors.

npm i react-hook-form@7



 const { register, handleSubmit } = useForm();

'register' is to register the inputs into this hook. So into the for using useForm() hook.

And 'register' is called using {...register("name")} where 'name' is the id in the iput tag of html. (as below). This is registering inputs to the form.


 <FormRow>
        <Label htmlFor="name">Cabin name</Label>
        <Input type="text" id="name" {...register("name")} />
   </FormRow>


Then we call 'onSubmit' by passing 'handleSubmit' using  'useForm' and inside 'handleSubmit' we pass the function which is to be called when the form is submitted.


<Form onSubmit={handleSubmit(submitForm)}>


function submitForm(data){

  }


'data' consists of all inputs being registered in the form using 'handleSubmit' in 'useForm' hook.
