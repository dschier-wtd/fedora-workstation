#!/usr/bin/env bash

# Are we in bash?
[ "${BASH_VERSION}" != "" ] || return 0

# Are we interactive?
[ "${PS1}" != "" ] || return 0

# apply .dotfiles configuration
for file in ~/.dotfiles/system/*; do
    # shellcheck source=/dev/null
    source "${file}"
done

# Powerline-Go
# Reference: https://github.com/justjanne/powerline-go

if [ -f "${GOPATH}"/bin/powerline-go ]; then
    function _update_ps1() {

        PS1=$("${GOPATH}"/bin/powerline-go -error $? -cwd-max-depth 3 -hostname-only-if-ssh -jobs "$(jobs -p | wc -l)")
        set "?"
    }

    if [ "${TERM}" != "linux" ] && [ -f "${GOPATH}/bin/powerline-go" ]; then
        PROMPT_COMMAND="_update_ps1; ${PROMPT_COMMAND}"
    fi
fi
