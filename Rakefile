require 'pathname'

task :default => :generate_css

desc "Generate css files from sass source."
task :generate_css do
  Dir.chdir(Pathname(__FILE__).dirname) do
    Pathname.glob('*.sass').reject do |f|
      f.basename.to_s.match(/^_/)
    end.each do |f|
      sh 'sass', f.basename, f.basename.to_s[0...-4] + 'css'
    end
  end
end