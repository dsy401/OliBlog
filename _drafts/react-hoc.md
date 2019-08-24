---
layout: post_layout
title: React HOC
date: 2019-08-24 11:00:00
location: Auckland
pulished: true
excerpt_separator: '```'
---

High-level components (HOC) are an advanced technique used in React to reuse component logic. The HOC itself is not part of the React API, it is a design pattern based on the combined nature of React. Specifically, a high-level component is a function whose parameters are components and whose return value is a new component.

For example:

```javascript
import React, {Component} from 'react';

const SchoolHoc = (fileds) => {
    return WrappedComponent => {
        return class extends Component{
            render(){
                return (
                    <WrappedComponent
                        {...this.props}
                        school={{...fileds}}
                    />
                )
            }
        }
    }
}

export default SchoolHoc
```

```javascript
import React from "react";
import DashboardLayout from "../../components/layout/dashboard_layout/dashboard_layout";
import { Switch, Route } from "react-router-dom";
import Content from './content/content'
import SchoolHoc from '../../hoc/SchoolHoc'

const Dashboard = props => {
  const schools = [
    {
      name: 'uoa',
    },
    {
      name: 'aut',
    },
    {
      name: 'massey',
    },
    {
      name: 'lincoln',
    },
    {
      name: 'otago',
    },
    {
      name: 'uc',
    },
    {
      name: 'victoria',
    },
    {
      name: 'waikato',
    }
  ]
  return (
    <DashboardLayout>
      <Switch>
        {schools.map((school,index)=>(
            <Route
                key={index}
                path={`${props.match.path}/${school.name}`}
                component={SchoolHoc({name: school.name})(Content)}
            />
        ))}
      </Switch>
    </DashboardLayout>
  );
};

export default Dashboard;
```
