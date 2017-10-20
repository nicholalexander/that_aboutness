require 'pry'

task :default do
  puts 'you have no default task'
end

namespace :jekyll do
  task :new_post, [:post_name] do |task, args|
    # create post filename
    time_stamp = Time.now.strftime("%Y-%m-%d")
    title = args[:post_name].tr(' ', '-')
    file_name = "#{time_stamp}-#{title}.md"
    
    # create front matter
    front_matter = YAML.load_file('./_data/front_matter_template.yml')
    front_matter["date"] = Date.parse(time_stamp)
    front_matter["title"] = args[:post_name]
    front_matter_formatted = front_matter.to_yaml + "---\n"

    # write file
    File.write("_posts/#{file_name}", front_matter_formatted)

    # open for editing
    system("subl _posts/#{file_name}")
  end

  task :deploy do
    puts "deploying to our server...."
  end
end