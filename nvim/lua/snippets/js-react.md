
local ls = require 'luasnip'
local s = ls.snippet
local t = ls.text_node
local i = ls.insert_node

return {
  -- Arrow function component
  s('rfc', {
    t { 'export const ' },
    i(1, 'ComponentName'),
    t ' = () => {',
    t { '', '  return (' },
    t { '', '    <div>' },
    i(2),
    t { '</div>', '  )' },
    t { '', '}' },
  }),

  -- useState básico
  s('usf', {
    t 'const [',
    i(1, 'state'),
    t ', ',
    i(2, 'setState'),
    t "] = useState('",
    i(3, ''),
    t "')",
  }),

  -- useEffect básico
  s('uef', {
    t { 'useEffect(() => {', '  ' },
    i(1, '// efeito'),
    t { '', '}, [])' },
  }),
}
