require 'rake'

desc "import users of type: First Last <first@email.com>"
task :import_from_email_type do
  filename = ENV.fetch("filename")
  puts "firstname,lastname,email"
  File.open(filename, "r") do |file|
    file.each do |line|
      cleaned_line = line.chomp
      if cleaned_line[-1] == ","
        cleaned_line = cleaned_line[0..-2]
      end
      name, email = cleaned_line.split("<").map(&:chomp)
      names = name.split("\s")
      email = email.chomp[0..-2]
      firstname = names[0]
      lastname = names[1..-1].join(" ")
      lastname = firstname if lastname.empty?
      puts "#{firstname},#{lastname},#{email}"
    end
  end
end

task :default => :import_from_email_type