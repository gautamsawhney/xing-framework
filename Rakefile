# vim: set ft=ruby :
require 'corundum/tasklibs'

module Corundum
  Corundum::register_project(__FILE__)

  core = Core.new

  core.in_namespace do
    GemspecFiles.new(core)

    #do |files|
      #files.extra_files = Rake::FileList["default_configuration/**/*"]
    #end

    #Also available: 'unfinished': TODO and XXX
    ["debug", "profanity", "ableism", "racism", "gender"].each do |type|
      QuestionableContent.new(core) do |content|
        content.type = type
      end
    end
    rspec = RSpec.new(core)
    SimpleCov.new(core, rspec) do |cov|
      cov.threshold = 40
    end

    gem = GemBuilding.new(core)
    GemCutter.new(core,gem)
    Git.new(core) do |vc|
      vc.branch = "master"
    end
  end
end

task :default => [:release, :publish_docs]
