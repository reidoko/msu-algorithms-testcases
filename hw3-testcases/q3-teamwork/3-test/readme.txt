The files are named according to the following:
<robot 0 color>-<robot 1 color>-<robot 2 color>_<robot being tested>

A bash script for testing this (feel free to modify this -- just don't ask me to make it work on your system):

for i in $(seq 0 2); do
    for j in $(seq 0 2); do
        for k in $(seq 0 2); do
            guess_0=$(python main.py<"3-test/$i-$j-${k}_0.txt")
            guess_1=$(python main.py<"3-test/$i-$j-${k}_1.txt")
            guess_2=$(python main.py<"3-test/$i-$j-${k}_2.txt")
            if [[ "$i" -eq "$guess_0" ]] || [[ "$j" -eq "$guess_1" ]] || [[ "$k" -eq "guess_2" ]]; then
                printf "$i,$guess_0 $j,$guess_1 $k,$guess_2: Correct\n"
            else
                printf "$i,$guess_0 $j,$guess_1 $k,$guess_2: Wrong\n"
            fi
        done
    done
done
