How to get sup to notify on new messages.

## hooks/after-poll.rb

      File: ~/.sup/hooks/after-poll.rb
      Executes immediately after a poll for new messages completes.
      Variables:
                         num: the total number of new messages added in this poll
                   num_inbox: the number of new messages added in this poll which
                              appear in the inbox (i.e. were not auto-archived).
      num_inbox_total_unread: the total number of unread messages in the inbox
               from_and_subj: an array of (from email address, subject) pairs
         from_and_subj_inbox: an array of (from email address, subject) pairs for
                              only those messages appearing in the inbox

Beep (Linux only) on new message (only if it's shown in the Inbox).

      if num_inbox > 0
        puts 7.chr
      end

