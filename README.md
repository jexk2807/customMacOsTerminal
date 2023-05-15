# customMacOsTerminal

command : killport [YOUR PORT]
```javascript
killport() {
    if [ -z "$1" ]
    then
        echo "No port supplied"
    else
        PIDS=$(sudo lsof -t -i:$1)
        if [ -z "$PIDS" ]
        then
            echo "No processes to kill"
        else
            for PID in $PIDS
            do
                kill -9 $PID
                echo "Killed process $PID on port $1"
            done
        fi
    fi
}
```
