# AlphLand API Client

TypeScript/JavaScript client for the AlphLand API.

## Installation

```bash
npm install alphland-api-client
```

## Usage

```tsx
import { Configuration, DAppDto, DAppsApi } from "@fugashu/alphland-api-client";
import { useEffect, useState } from "react";

// Initialize
const api = new DAppsApi(
  new Configuration({
    basePath: "https://publicapi.alph.land", // or 'http://localhost:3000' for local dev
  })
);

// React example
export function DAppList() {
  const [dapps, setDapps] = useState<DAppDto[]>([]);

  useEffect(() => {
    api
      .dAppControllerGetAllDapps()
      .then(({ data }) => setDapps(data))
      .catch(console.error);
  }, []);

  return (
    <div>
      {dapps.map((dapp) => (
        <div key={dapp.name}>
          <h2>{dapp.name}</h2>
          <img src={dapp.media.logoUrl} alt={`${dapp.name} logo`} />
        </div>
      ))}
    </div>
  );
}
```
