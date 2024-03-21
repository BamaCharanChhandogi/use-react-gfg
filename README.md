# use-react-GFG

> A tiny fully customizable react hook which gives you full profile details of Geeks for Geeks coder.

[![NPM](https://img.shields.io/npm/v/use-react-gfg.svg)](https://www.npmjs.com/package/use-react-gfg) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

## Install

- npm

```bash
npm install use-react-gfg
```

- yarn

```bash
yarn add use-react-gfg
```

<!-- ## Examples -->

<!-- See this [codesandbox](https://codesandbox.io/s/use-react-countries-examples-forked-tf85v?file=/Readme.md) playground or /example folder if you want to play with hook. -->

## Usage

A simple example of a component which you can copy-paste and take info about all Profiles.

```jsx
import React, { useEffect } from "react";
import {useGFG} from "use-react-gfg";

function ProfileInterface() {
  const { profile, loading, error } = useGFG("bamacharan");

  useEffect(() => {
    console.log("Profile Data:", profile);
  }, [profile]);

  if (loading) {
    return <div>Loading...</div>;
  }

  if (error) {
    return <div>{error}</div>;
  }

  if (!profile || !profile.info) {
    return <div>Error: Profile data not found.</div>;
  }

  const { info, solvedStats } = profile;

  return (
    <div className="profile">
      <div className="basic-info">
        <h1>{info.userName}'s Profile</h1>
        {info.profilePicture && (
          <img src={info.profilePicture} alt="Profile Picture" />
        )}
        <p>Institute Rank: {info.instituteRank}</p>
        <p>Current Streak: {info.currentStreak}</p>
        <p>Max Streak: {info.maxStreak}</p>
        <p>Languages Used: {info.languagesUsed}</p>
      </div>

      <div className="solved-stats">
        <h2>Solved Stats</h2>
        <ul>
          {Object.entries(solvedStats).map(([difficulty, stats]) => (
            <li key={difficulty}>
              <h3>{difficulty}</h3>
              <p>Count: {stats.count}</p>
              {/* You can render individual questions here if needed */}
            </li>
          ))}
        </ul>
      </div>
    </div>
  );
}

export default ProfileInterface;
```

## API

- Profile interface

```javascript
{
  "info": {
    "userName": "string",
    "profilePicture": "string",
    "instituteRank": "string",
    "currentStreak": "string",
    "maxStreak": "string",
    "institution": "string",
    "languagesUsed": "string",
    "codingScore": "string",
    "totalProblemsSolved": "string",
    "monthlyCodingScore": "string",
    "articlesPublished": "string"
    // Add any additional fields as needed
  },
  "solvedStats": {
    "school": {
      "count": "number",
      "questions": [
        {
          "question": "string",
          "questionUrl": "string"
        }
      ]
    },
    "basic": {
      "count": "number",
      "questions": [
        {
          "question": "string",
          "questionUrl": "string"
        }
      ]
    },
    "easy": {
      "count": "number",
      "questions": [
        {
          "question": "string",
          "questionUrl": "string"
        }
      ]
    },
    "medium": {
      "count": "number",
      "questions": [
        {
          "question": "string",
          "questionUrl": "string"
        }
      ]
    },
    "hard": {
      "count": "number",
      "questions": [
        {
          "question": "string",
          "questionUrl": "string"
        }
      ]
    }
  }
}

```

<!-- | Property           | Type                                           | Description |
| ------------------ | ---------------------------------------------- | ----------- |
| name               | string                                         |             |
| capital            | string                                         |             |
| area               | number                                         |             |
| emoji              | string                                         |             |
| flags              | { png: string, svg: string }                   |             |
| countryCallingCode | number                                         |             |
| population         | number                                         |             |
| currencies         | { name: string, symbol: string }[]             |             |
| languages          | string[]                                       |             |
| maps               | { googleMaps: string, openStreetMaps: string } |             |
| postalCode         | { format: string, regex: string }              |             |
| coordinates        | [number, number]                               |             | -->

## Authors

- [Bama Charan Chhandogi](https://linktr.ee/bamacharan)

## License

MIT © [vre2h](https://github.com/BamaCharanChhandogi)

---
