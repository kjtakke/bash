you can either use
 
tput smcup to switch
and tput rmcup to switch back
 
or if using ansi on xterm you can do
`echo -e "\e[?1049h"`
`echo -e "\e[?1049l"`
 