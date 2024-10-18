# Directory Structure

Our project is organised into a number of different directories which serve different purposes:

- **Client**
- **Server**
- **Shared:** contains code shared between both the client and the server
- **vendor:** unmodified third-party code and libraries (optionally linked to the appropriate third-party Git repository through Git submodules). 

## Projects explained

### Client projects
- **Client Core:** Typically UI elements like main menu etc and isn't ever unloaded.

- **Client Deathmatch:** Where MTA makes all it's functions and events do stuff.

- **Client Launcher:** Is the MTA executable which loads loader, you need not touch.

- **Client SDK:** no info.

- **Client Webbrowser:** related to CEF.

- **Game SA:** Low level stuff which is mainly function calls to the game so each element will have a game_sa class like Vehicle, Ped, Object etc.

- **GUI:** It's just wrappers to [CEGUI](https://github.com/cegui/cegui), you need not touch.

- **Loader:** You need not touch the loader either.

- **Loader Proxy**: related to loader.

- **Multiplayer SA:** Hooks, code modification and that sort of low level things that lets us work.

### Server projects
- **Core:** Cazomino05: ***I genuinely don't really know why we have server core.***

- **Dbconmy:** Stuff to do with the db* functions, you need not touch.

- **Deathmatch:** All the server logic and storage classes for elements as well as Lua stuff.

- **Launcher:** Just an executable to load all the DLLs we need.

- **SDK:** no info.

### Shared projects
- **Shared** utility functions

- **XML:** XML module is just tinyxml and some high level wrapper functions for stuff we need.


