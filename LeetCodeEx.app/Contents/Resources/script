require 'net/http'
require 'json'
require 'terminal-notifier'


# LeetCode API's base URL
base_url = 'https://leetcode.com/api/problems/all/'

# Set the timer to fetch a LeetCode problem and send a notification every 4 hours (in seconds)
notification_interval_seconds = 4 * 60 * 60

# Define the time frame during which notifications are muted (10 pm to 8 am)
mute_start_time = 22 # 10 pm (24-hour format)
mute_end_time = 8    # 8 am (24-hour format)

loop do
  # Get the current hour
  current_hour = Time.now.hour

  # Check if notifications should be muted during the specified time frame
  if current_hour >= mute_start_time || current_hour < mute_end_time
    puts 'Notifications are muted during the specified time frame.'
  else
    # Use an HTTP GET request to fetch LeetCode problem data
    uri = URI(base_url)
    response = Net::HTTP.get(uri)
    data = JSON.parse(response)

    # Filter out locked problems and get the difficulty level
    unlocked_problems = data['stat_status_pairs'].reject { |problem| problem['paid_only'] }
    if unlocked_problems.count > 0
      random_problem = unlocked_problems.sample
      title = random_problem['stat']['question__title']
      difficulty = case random_problem['difficulty']['level']
                   when 1
                     'Easy'
                   when 2
                     'Medium'
                   when 3
                     'Hard'
                   else
                     'Unknown'
                   end

      # Build the problem link
      problem_link = "https://leetcode.com/problems/#{title.downcase.tr(' ', '-')}"

      # Build notification content with the -open option
      notification_options = {
        title: 'LeetCode Problem Notification',
        subtitle: "Difficulty: #{difficulty}",
        sound: 'default', # You can set the notification sound
        open: problem_link  # Use the -open option to make the notification clickable
      }

      # Send the notification without including the problem link in the message
      TerminalNotifier.notify("#{title}", notification_options)
    else
      puts 'No unlocked problems available.'
    end
  end

  # Sleep for the specified notification interval
  sleep notification_interval_seconds
end


