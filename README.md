## Build number tracker for SideStore CI builds.
This repo serves as a counter for github CI actions used by sidestore repo.  
SideStore GH Action cross posts the build number it reserves during build so that it can increment from there for next runs.  

### Synchronization Strategies
- CI action workflows should handle retry when a build number they fetched and updater locally is not available for push if any other workflow updated it in meantime by trying to push again after rebasing each time with n retry attempts during contention.


### Current Structure and Expectations
- each action from a specific branch will use same branch in this repo, and since CI are sequential per ref/branch, they provide adequate serialization.

### Sample output json
```json
{
  "build": 17,
  "issued_at": "2026-02-23T23:57:54Z",
  "tag": "nightly"
}
```
