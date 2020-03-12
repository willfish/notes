# Notes

Keeps my notes in version control so that what I write each day is in a standardised format.

### Prerequisites

- vim
- fish shell (although really any shell :))


### Convenience functions

```fish
function today -d "Open today's notes"
  set -l todays_date (date +%F)
  set -l notes_directory "$HOME/Notes/$todays_date"
  set -l note_file "$notes_directory/today.md"
  set -l template_file "$HOME/Notes/templates/today.md"

  if not test -e $note_file
    mkdir -p $notes_directory
    cp $template_file $note_file
    sed -i "s/TodaysDate/$todays_date/" $note_file
  end

  vim $note_file
end

function standup -d "Open today's standup notes"
  set -l todays_date (date +%F)
  set -l notes_directory "$HOME/Notes/$todays_date"
  set -l note_file "$notes_directory/standup.md"
  set -l template_file "$HOME/Notes/templates/standup.md"

  if not test -e $note_file
    mkdir -p $notes_directory
    cp $template_file $note_file
    sed -i "s/TodaysDate/$todays_date/" $note_file
  end

  vim $note_file
end
```
