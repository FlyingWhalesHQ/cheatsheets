---
layout: default
title: Validations
parent: Rails
nav_order: 2
---

{% include toc.md title="Rails Validations Cheatsheets" %}

## Builtin Validators

```rb
class Player < ApplicationRecord
  validates :terms_of_service, acceptance: true

  validates :name, :address, presence: true
  validates :password, confirmation: true

  # numericality validation does not allow nil value
  # use allow_nil: true to permit it
  validates :points, numericality: true
  validates :games_played, numericality: { only_integer: true }
  # other options:
  # :greater_than
  # :greater_than_or_equal_to
  # :equal_to
  # :less_than
  # :less_than_or_equal_to
  # :other_than
  # :odd
  # :even
end
```

## Conditional Validations

```rb
class User < ApplicationRecord
  validates :password, confirmation: true,
    unless: Proc.new { |a| a.password.blank? }
  validates :name, if: :active?

  # Group similar conditional validation
  with_options if: :is_admin? do |admin|
    admin.validates :password, length: { minimum: 10 }
    admin.validates :email, presence: true
  end
end
```

---

## Custom validators

These custom validators should be placed in app/validators

__Validate object as a whole__

```rb
class MyValidator < ActiveModel::Validator
  def validate(record)
    unless record.name.starts_with? 'X'
      record.errors[:name] << 'Need a name starting with X please!'
    end
  end
end

class Person < ActiveRecord::Base
  validates_with MyValidator
end
```

__Validate individual attribute__

```rb
class EmailValidator < ActiveModel::EachValidator
  def validate_each(record, attribute, value)
    unless value =~ /\A([^@\s]+)@((?:[-a-z0-9]+\.)+[a-z]{2,})\z/i
      record.errors[attribute] << (options[:message] || "is not an email")
    end
  end
end

class Person < ActiveRecord::Base
  validates :email, presence: true, email: true
end
```

---

## Custom validation methods

```rb
class Event < ApplicationRecord
  validate :start_date_must_be_before_end_date

  private

  def start_date_must_be_before_end_date
    if start_date > end_date
      errors.add(:base, "start date must be before end date")
    end
  end
end
```

---

## Resources

- [Active Record Validations](https://guides.rubyonrails.org/active_record_validations.html)
- [The Perils of Uniqueness Validations](https://thoughtbot.com/blog/the-perils-of-uniqueness-validations)
- [ValidatesTimeliness gem](https://github.com/adzap/validates_timeliness)
