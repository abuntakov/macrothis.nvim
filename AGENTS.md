# Agent Guidelines for macrothis.nvim

## Build/Lint/Test Commands
- **Format**: `make fmt` or `stylua lua/ --config-path=.stylua.toml`
- **Lint**: `make lint` or `luacheck lua/telescope`
- **Generate docs**: `make documentation` (requires mini.nvim in deps/)
- **No tests**: This project does not have automated tests

## Code Style
- **Language**: Lua (LuaJIT standard)
- **Formatting**: Use StyLua with 4 spaces, 80 column width, double quotes preferred
- **Imports**: Use `require()` at the top of files; use `pcall(require, ...)` for optional dependencies
- **Naming**: Use snake_case for functions and variables (e.g., `load_macro`, `run_register`)
- **Documentation**: Use LuaCATS annotations (`---@usage`, `---@eval`, `---@tag`) for public functions
- **Global**: Only `vim` is allowed as a read-only global (defined in .luacheckrc)
- **Error handling**: Use `pcall()` for optional dependencies; check file operations with `if not fd then` patterns
- **Module pattern**: Return table with functions; use local tables (e.g., `local utils = {}`)
- **API calls**: Use `vim.api.*`, `vim.fn.*`, `vim.ui.*` for Neovim interactions
- **String formatting**: Use `("%s: %s"):format(...)` for string interpolation
- **Tables**: Use descriptive keys in table constructors (e.g., `{ label = key, value = val }`)

## Project Structure
- `lua/macrothis/`: Core plugin code (init.lua, utils.lua, base64.lua)
- `lua/telescope/_extensions/`: Telescope integration
- `doc/`: Vimdoc documentation (auto-generated with mini.doc)
